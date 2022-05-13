NodePort
---
🏠 [Home](/workshops/services/README.md)

## Create a service of type NodePort

Using `create service` command
```
kubectl create service nodeport logga-nodeport -n logga --tcp=8080:8080
```

Using `kubectl expose` command
```
kubectl expose deployment logga \
  -n logga \
  --name=logga-nodeport \
  --type=NodePort
  --port=8080 \
  --target-port=8080
```

Using `kubectl apply` for more control.
```yaml
cat <<EOF | k apply -f -
apiVersion: v1
kind: Service
metadata:
  name: logga
  namespace: logga
spec:
  type: LoadBalancer
  ports:
  - name: http
    port: 8080
    protocol: TCP
    targetPort: 8080
  selector:
    app: logga
EOF
```

## Verify

See the service
```
kubectl get service -n logga
```

Inspect the service
```
kubectl describe service logga -n logga
```

Access the app through the service
```
kubectl port-forward service/logga -n logga 8080:8080
```