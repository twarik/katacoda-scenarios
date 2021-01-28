To deploy a model we create following resources
- A deployment to deploy the model using TFServing
- A K8s service to create an endpoint a service
- An Istio virtual service to route traffic to the model and expose it through the Istio gateway
- An Istio DestinationRule is for doing traffic splitting.

Clone this manifests to create resources for our deployment and serve the model.

`curl -s https://github.com/twarik/maven/resources.yaml`{{execute}}

Create resources
`microk8s kubectl create -f resources.yaml`{{execute}}
