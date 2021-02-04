Create a Deployment,  Service, VirtualService and DestinationRule.

<!-- We create the above resources using a yaml file.

`wget https://raw.githubusercontent.com/twarik/maven/main/resources.yaml`{{execute}}

Have a look at the yaml file content

`cat ./resources.yaml`{{execute}} -->

We use a manifest to create resources via Kubectl.

`kubectl create -f https://raw.githubusercontent.com/twarik/maven/main/resources.yaml`{{execute}}

View the status of the deployment:

`kubectl get deployments`{{execute}}

View the status of the pods:

`kubectl get pods`{{execute}}

View the status of the service:

`kubectl get services`{{execute}}

It can take a while for everything to be up and running.

`kubectl describe service customer-churn-service`{{execute}}

The service external IP address is listed next to LoadBalancer Ingress


### Creating the Ingress Resource

`kubectl apply -f https://raw.githubusercontent.com/twarik/maven/main/ingress.yaml`{{execute}}

Obtaining the External IP Address of the Load Balancer

To confirm the `customer-churn service` is running as a `LoadBalancer` service, obtain its external IP address by entering:

`kubectl get svc --all-namespaces`{{execute}}

### Configure Ingress
To allow incoming traffic into our “mesh”, we need to setup an ingress Gateway. Our Gateway that will act as a load balancing proxy by exposing port 31400 to receive traffic:

`kubectl create -f https://raw.githubusercontent.com/twarik/maven/main/gateway.yaml`{{execute}}
