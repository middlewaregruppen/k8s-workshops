Deployments
---
🏠 [Home](/README.md)

A Kubernetes `deployment` is a resource in Kubernetes that provides declarative updates to applications. A deployment allows you to describe an application’s life cycle, such as which images to use for the app, the number of pods there should be, and the way in which they should be updated. 

## Creating Deployments with `kubectl create`

Create a deployment in a namespace using `kubectl`
```
kubectl create namespace logga
kubectl create deployment logga --namespace logga --image=amimof/logga:latest --port=8080
```

## Creating Deployments with `kubectl apply`

Save following to the file `deployment.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: logga
  name: logga
  namespace: logga
spec:
  replicas: 1
  selector:
    matchLabels:
      app: logga
  template:
    metadata:
      labels:
        app: logga
    spec:
      containers:
      - image: amimof/logga:latest
        name: logga
        ports:
        - containerPort: 8080
          protocol: TCP
```

Apply the deployment
```
kubectl apply -f deployment.yaml
```

## Verifying

See what we created
```
kubectl get deployment -n logga
```

Inspect the deployment
```
kubectl get deployment logga -n logga -o yaml
```
> Pro Tip! You can output (-o) to a number of different formats including `json|yaml|name|go-template|go-template-file|template|templatefile|jsonpath|jsonpath-as-json|jsonpath-file|custom-columns-file|custom-columns|wide` 

The deployment automatically creates a `ReplicaSet`
```
kubectl get replicaset -n logga
```

The ReplicaSet ultimately creates `Pods`
```
kubectl get pods -n logga
```

## Scaling
Scale up the deployment with `kubectl scale` command
```
kubectl scale deployment logga -n logga --replicas=2
```

Scale down the deployment by updating the `replicas` field in the `Deployment` resource
```
kubectl edit deployment logga -n logga
```

Scale up the deployment again with `kubectl patch` command
```
kubectl patch deployment logga -p '{"spec":{"replicas":3}}'
```

## Making changes
Make a change to the deployment to trigger a new rollout
```
kubectl set env deployment/logga -n logga MY_ENV_VAR=somevalue
```

Watch as the new version is rolled out
```
kubectl rollout status deployment/logga -n logga
```