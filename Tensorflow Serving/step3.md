To deploy a model we create the following resources
- A deployment to deploy the model using TFServing
- A K8s service to create an endpoint a service
- An Istio virtual service to route traffic to the model and expose it through the Istio gateway
- An Istio DestinationRule is for doing traffic splitting.

We create the above resources using the Kubernetes config resources.yaml.

Install wget package
`apt install wget`{{execute}}

Download the yaml manifest for creating resources

`wget https://raw.githubusercontent.com/twarik/maven/main/resources.yaml`{{execute}}

Have a look at the yaml file content

`cat ./resources.yaml`{{execute}}

## Deployed via Kubectl

Create resources using the config resources.yaml

<!-- `microk8s kubectl create -f ./resources.yaml`{{execute}} -->
`kubectl create -f ./resources.yaml`{{execute}}

The output should look like:

`deployment "resnet-deployment" created
service "resnet-service" created`

view the status of the deployment:

`kubectl get deployments`{{execute}}

view the status of the pods:

`kubectl get pods`{{execute}}

view the status of the service:

`kubectl get services`{{execute}}

It can take a while for everything to be up and running.

`kubectl describe service half-plus-two-service`{{execute}}

The service external IP address is listed next to LoadBalancer Ingress
