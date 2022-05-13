Deploying a Load Balancer
---
🏠 [Home](/workshops/preparations/README.md)

Load balancers in Kubernetes allows to access our services that are running inside the cluster. There are many load balancer implementations, we are going to use `MetalLB`. MetalLB is a load-balancer implementation for bare metal Kubernetes clusters, using standard routing protocols.

## Deploy

1. Create the namespace
   ```
   kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.12.1/manifests/namespace.yaml
   ```
2. Deploy metallb
   ```
   kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.12.1/manifests/metallb.yaml
   ```
3. Wait for metallb pods to run
   ```
   kubectl wait \
    --namespace metallb-system \
    --for=condition=ready pod \
    --selector=app=metallb \
    --timeout=90s
   ```
4. Setup address pool used by Load Balancers
   ```
   docker network inspect -f '{{.IPAM.Config}}' kind
   ```
5. Configure the address pool used for the load balancers
   ```yaml
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: metallb-system
  name: config
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - 172.18.255.200-172.18.255.250
EOF
   ```

## Verify

1. Create a Service of type `LoadBalancer`
   ```
   kubectl create service loadbalancer my-lbs --tcp=5678:8080
   ```
2. Make sure the loadbalancer is given an `External-IP` address
   ```
   kubectl get service my-lbs
   ```