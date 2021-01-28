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
    software-properties-common


    `{{execute}}

## Install TensorFlow Serving


**Add TensorFlow Serving distribution URI as a package source:**

`echo "deb http://storage.googleapis.com/tensorflow-serving-apt stable tensorflow-model-server tensorflow-model-server-universal" | tee /etc/apt/sources.list.d/tensorflow-serving.list && \
curl https://storage.googleapis.com/tensorflow-serving-apt/tensorflow-serving.release.pub.gpg | apt-key add -
apt update`{{execute}}

This is all you need - one command line!

`apt-get install tensorflow-model-server`{{execute}}
