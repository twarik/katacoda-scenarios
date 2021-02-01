Given that we are running a Kubernetes cluster on a bare metal (private k8s cluster), we need to install **MetalLB** to expose the cluster services on a dedicated IP address on the network.

Alternatively, If you were using microk8s, you would just enable this add on and provide the IP address pool in the enable command:

microk8s enable metallb:x.x.x.x-x.x.x.x

For cloud users (EKS, GKE), Google Cloud or AWS would do it

If it is your private k8s cluster, MetalLB would be a better fit. Below are the steps.

## Step 1: Install MetalLB in your cluster

```
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/namespace.yaml

kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.3/manifests/metallb.yaml

# On first install only
kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"
```{{execute}}

Step 2: Configure the MetalLB by using a configmap

`kubectl apply -f https://raw.githubusercontent.com/twarik/maven/main/metallb.yml`{{execute}}

Step 3: Create your service to get an external IP (would be a private IP though).
