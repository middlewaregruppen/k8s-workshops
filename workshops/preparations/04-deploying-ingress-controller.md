Deploying an ingress controller
---
🏠 [Home](/workshops/preparations/README.md)

An [ingress controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/) is the component that allows requests from outside the cluster to reach our services inside the cluster.

## Deploy
We'll be using [nginx](https://github.com/traefik/traefik) as our ingress controller. Run the following to deploy it in your cluster.
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

Then `wait` for the deployment to finish (this will timeout)
```
kubectl wait \
  --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s
```

Label the nodes so that they the deployment "accept" the nodes. Run the `wait` command again
```
kubectl label node kind-worker kind-worker2 kind-worker3 ingress-ready=true
```
> Pro Tip! You may pass in node labels during cluster creation using `kubeletExtraArgs` in the kind configuration file

## Verify that nginx is up and running
```
kubectl get pods --namespace ingress-nginx
```
> Pro Tip! You can shorten the `--namespace` flag to `-n`
