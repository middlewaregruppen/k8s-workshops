Creating a Kubernetes cluster
---
🏠 [Home](/workshops/preparations/README.md)

We will be using `kind` to create a cluster throughout the majority of the workshops. Kind is short for *kubernetes in docker* and as implied by the name, your entire clusters is run inside of containers using `Docker`. If you have not already installed Kind & Docker, make sure to to check out [Installing Client Tools](./install-client-tools.md)

## Create a basic single node cluster
Creates a single node cluster named `kind`. But we need to pass in some configuration so read on.
```
kind create cluster
```

## Create a cluster with configuration
Creates a cluster with 3 nodes
```yaml
cat <<EOF | kind create cluster --config=-
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: TCP
  - containerPort: 443
    hostPort: 443
    protocol: TCP
EOF
```

## What you get
When the cluster create command completes you should see the following in your terminal
```
$ kind create cluster
Creating cluster "kind" ...
 ✓ Ensuring node image (kindest/node:v1.21.1) 🖼
 ✓ Preparing nodes 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
Set kubectl context to "kind-kind"
You can now use your cluster with:

kubectl cluster-info --context kind-kind

Not sure what to do next? 😅  Check out https://kind.sigs.k8s.io/docs/user/quick-start/
```

## Verify connectivity
Now it's time to issue our first commands to our new cluster. For this we need `kubectl`. Make sure to have that installed first.

Get cluster info
```
kubectl cluster-info
```

List the nodes in your cluster
```
kubectl get nodes
```