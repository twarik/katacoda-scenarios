Rolling out model

Use Istio.

Here is how it works:
The first thing to do is deploy a model A. Then we develop another model B, and we want to deploy it and gradually move traffic from A to B. This can be achieved using Istio’s traffic routing.

1. Deploy the first model as described for TensorFlow Serving. Then you will have the service (Model) and the deployment (Version).
2. Deploy another version of the model, v2. This time, no need to deploy the service part.

```
MODEL_COMPONENT2=mnist-v2

KF_ENV=default

ks generate tf-serving-deployment-gcp ${MODEL_COMPONENT2}

ks param set ${MODEL_COMPONENT2} modelName mnist  // modelName should be the SAME as  the previous one

ks param set ${MODEL_COMPONENT2} versionName v2   // v2 !!

ks param set ${MODEL_COMPONENT2} modelBasePath gs://kubeflow-examples-data/mnist

ks param set ${MODEL_COMPONENT2} gcpCredentialSecretName user-gcp-sa

ks param set ${MODEL_COMPONENT2} injectIstio true   // This is required

ks apply ${KF_ENV} -c ${MODEL_COMPONENT2}
```{{execute}}

3. Update the traffic weight

```
ks param set mnist-service trafficRule v1:90:v2:10   // This routes 90% to v1, and 10% to v2

ks apply ${KF_ENV} -c mnist-service
```{{execute}}
