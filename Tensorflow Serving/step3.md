To deploy a model we create the following resources
- A deployment to deploy the model using TFServing
- A K8s service to create an endpoint a service
- An Istio virtual service to route traffic to the model and expose it through the Istio gateway
- An Istio DestinationRule is for doing traffic splitting.

<!-- `git clone https://github.com/twarik/katacoda-scenarios.git`{{execute}}

`cat ./katacoda-scenarios/resources.yaml`{{execute}}

## Deployed via Kubectl

Create resources

`microk8s kubectl create -f ./katacoda-scenarios/resources.yaml`{{execute}} -->

Download the yaml manifest for creating resources

Install wget package
`apt install wget`{{execute}}

Download the yaml manifest

`wget https://raw.githubusercontent.com/twarik/maven/main/resources.yaml`{{execute}}

View the yaml containing specs for creating resources

`cat ./resources.yaml`{{execute}}

## Deployed via Kubectl

Create resources

`microk8s kubectl create -f ./resources.yaml`{{execute}}
