Create a Deployment,  Service, VirtualService and DestinationRule.

We leverage a manifest to create the above k8s resources

`kubectl create -f https://raw.githubusercontent.com/twarik/maven/main/resources.yaml`{{execute}}

view the status of the deployment:

`kubectl get deployments`{{execute}}

view the status of the pods:

`kubectl get pods`{{execute}}

view the status of the service:

`kubectl get services`{{execute}}

It can take a while for everything to be up and running.

`kubectl describe service customer-churn-service`{{execute}}

The service external IP address is listed next to LoadBalancer Ingress
