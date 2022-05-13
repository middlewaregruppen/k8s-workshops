Troubleshooting the application
---
🏠 [Home](/workshops/troubleshooting/README.md)

First deploy an app to troubleshoot
```yaml
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: multi-pod
spec:
  restartPolicy: Always
  volumes:
  - name: shared-data
    emptyDir: {}
  containers:
  - name: nginx
    image: nginx
    ports:
    - name: http
      containerPort: 80
      protocol: TCP
    volumeMounts:
    - name: shared-data
      mountPath: /usr/share/nginx/html
  - name: busybox
    image: busybox:1.28
    volumeMounts:
    - name: shared-data
      mountPath: /pod-data
    command: ["/bin/sh"]
    args: ["-c", "while true; do date >> /pod-data/index.html && sleep 1; done"]
EOF
```

## Logs
Print the pod logs
```
kubectl get pods 
kubectl logs multi-pod
```

Print pod logs (multi-container)
```
kubectl logs multi-pod -c nginx 
```

Stream pods logs
```
kubectl logs multi-pod -c nginx -f
```

Print pod logs for a previous instantiation of a container
```
kubectl logs multi-pod -c nginx --previous
```

## Executing commands inside container

Run a simple command
```
kubectl exec multi-pod -c busybox -- ls /pod-data
```

Interactive shell 
```
kubectl exec --tty -i multi-pod -c busybox -- sh
```
> Pro Tip! `--tty` can be shortened to just `-ti`

Attach to current process inside container
```
kubectl attach multi-pod -c nginx
```

