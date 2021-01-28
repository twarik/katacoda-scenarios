Before getting started, first install kubernetes, docker and tensorflow model server.

## Install kubernetes

We will use microk8s (a Low-ops, minimal production Kubernetes) to install Kubeflow for our scenario.

`sudo snap install microk8s --classic`{{execute}}

Turn on kubeflow and other services we want.
`microk8s enable dashboard dns registry istio
microk8s enable kubeflow`{{execute}}

Check the status while Kubernetes starts
`microk8s status --wait-ready`{{execute}}


## Install docker

`apt-get update
apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
apt-key fingerprint 0EBFCD88
add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io`{{execute}}

Verify that Docker Engine is installed correctly by running the hello-world image.
`docker run hello-world`{{execute}}

## Install TensorFlow model server


**Add TensorFlow Serving distribution URI as a package source:**

`echo "deb http://storage.googleapis.com/tensorflow-serving-apt stable tensorflow-model-server tensorflow-model-server-universal" | tee /etc/apt/sources.list.d/tensorflow-serving.list && \
curl https://storage.googleapis.com/tensorflow-serving-apt/tensorflow-serving.release.pub.gpg | apt-key add -
apt update`{{execute}}

Install model server !

`apt-get install tensorflow-model-server`{{execute}}