Before getting started, first install kubernetes, docker and tensorflow model server.

## Install kubernetes

we will use microk8s (a Low-ops, minimal production Kubernetes) to install Kubeflow for our scenario.

## Install docker

`apt-get update`{{execute}}
`apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common`{{execute}}

## Install TensorFlow Serving

This is all you need - one command line!

`apt-get install tensorflow-model-server`{{execute}}
