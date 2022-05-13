Ingresses
---
🏠 [Home](/README.md)

`Ingress` is a resource that manages external access to the services in a cluster, typically HTTP. Ingress may provide load balancing, SSL termination and name-based virtual hosting. Think of it as a Layer 7 load balancer interface.

## Creating ingresses with `kubectl create`
```
kubectl create ingress logga --rule="logga.foo.bar/*=logga:8080" -n logga
```

## Creating ingresses with `kubectl apply`

```yaml
cat <<EOF | k apply -f -
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: logga
  namespace: logga
spec:
  rules:
  - host: logga.foo.bar
    http:
      paths:
      - backend:
          service:
            name: logga
            port:
              number: 8080
        path: /
        pathType: Prefix
EOF
```

## Verifying

See what we created
```
kubectl get ingress -n logga
```

Inspect the ingress
```
kubectl get ingress logga -n logga -o yaml
```
> Pro Tip! You can output (-o) to a number of different formats including `json|yaml|name|go-template|go-template-file|template|templatefile|jsonpath|jsonpath-as-json|jsonpath-file|custom-columns-file|custom-columns|wide` 