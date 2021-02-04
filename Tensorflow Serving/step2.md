We need to install **MetalLB** to expose the cluster services on a dedicated IP address on the network.
<!-- If you were using microk8s, you would just enable this add-on and provide the IP address pool in the enable command: `microk8s enable metallb:x.x.x.x-x.x.x.x` -->

<!-- For cloud users (EKS, GKE), Google Cloud or AWS would do it -->
## Step 1: Install MetalLB in our cluster
```
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/namespace.yaml

kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/metallb.yaml

kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
```{{execute}}

## Step 2: Configure MetalLB

`kubectl apply -f https://raw.githubusercontent.com/twarik/maven/main/metallb.yml`{{execute}}

The next step is to create our service to get an external IP (would be a private IP though).

### Configure Ingress
To allow incoming traffic into our “mesh”, we need to setup an ingress Gateway. Our Gateway that will act as a load balancing proxy by exposing port 31400 to receive traffic:

`kubectl create -f https://raw.githubusercontent.com/twarik/maven/main/gateway.yaml`{{execute}}
