What the **** is going on?
---
🏠 [Home](/workshops/troubleshooting/README.md)

Whenever you encounter unpredicted behaviour of any kind in the cluster it is important to know where to start looking. Most of the times you can narrow it down by using basic `kubectl` commands. In this guide we will do just that

## Getting stuff
Simple get pods
```
kubectl get pods
```

Wide ouput gives more info
```
kubectl get pods -o wide
```

Output raw objects for full info
```
kubectl get pods -o yaml
```

Getting `all` does not get **all**
```bash
# Be mindful of this
kubectl get all
```

Check events 
```
kubectl get events
```

Check event by name
```
kubectl get events --field-selector involvedObject.name=ingress-nginx-controller-56d4b5df54-wgr9g
```

Watching resources
```
kubectl get events -w
```

## Describing stuff
```
kubectl describe pod ingress-nginx-controller-56d4b5df54-wgr9g
```

## Other things you can do
Is my cluster responding?
```
kubectl cluster-info
```

Cluster Resources
```
kubectl api-resources
```

Cluster API versions
```
kubectl api-versions
```

Cluster version
```
kubectl version
```