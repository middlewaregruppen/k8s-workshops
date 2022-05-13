Troubleshooting network
---
🏠 [Home](/workshops/troubleshooting/README.md)

## Connectivity
Try the URL
```
curl -v https://awesomeapp.amimof.com
```

Try the ingress
```
curl -v --resolve=awesomeapp.amimof.com https://10.84.0.241
```

Try the service
```
kubectl port-forward -n ingress-nginx service/ingress-nginx-controller 8443:443
curl -v https://127.0.0.1:8443 -k
```

Try the pod 
```bash
kubectl port-forward -n ingress-nginx pod/ingress-nginx-controller-56d4b5df54-wgr9g 8443:443
curl -v https://127.0.0.1:8443 -k
```
> Make sure you forward to correct pod port as it may not be the same as the service

## Pod-to-Pod
Running a *troubleshooting* pod
```
kubectl get pods -o wide
kubectl run --rm -i --tty busybox --image=busybox:1.28 -- sh
```

Ping
```
ping 10.244.1.4
```

wget/curl
```
wget 10.244.1.4
```

## DNS
```bash
kubectl run dnsutils\
  --rm \
  -i \
  --tty \
  --image=k8s.gcr.io/e2e-test-images/jessie-dnsutils:1.3 \
  -- nslookup kubernetes.default
```