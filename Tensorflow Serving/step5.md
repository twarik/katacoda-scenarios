Rolling out model

Use Istio.

Here is how it works:
The first thing to do is deploy a model A. Then we develop another model B, and we want to deploy it and gradually move traffic from A to B. This can be achieved using Istio’s traffic routing.

1. Deploy the first model as described for TensorFlow Serving. Then you will have the service (Model) and the deployment (Version).
2. Deploy another version of the model, v2. This time, no need to deploy the service part.
3. Update the traffic weight
