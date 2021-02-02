Say, we want to deploy a new TensorFlow model version  serving binary. Making changes to model deployments should always be done in an iterative way such that the new model behavior and performance can be properly tested.

**Upload the new version of the model to the location where you've saved your model.**

`wget -qO- https://github.com/twarik/maven/blob/main/saved_model_customer_churn/2.zip?raw=true | bsdtar -xvf- -C ~/saved_model_customer_churn`{{execute}}

**Apply the deployment to the cluster:**

`kubectl apply -f https://raw.githubusercontent.com/twarik/maven/main/resources_2.yaml`{{execute}}

**Update the traffic weight (Setup V2 Canary Routing)**

Now that we have our new model deployment, we would like to gradually roll it out to a subset of the users.
This can be done by updating our `VirtualService` to route a small % of traffic to `v2` subset.

We will be cautious and update our `VirtualService` to route 30% of incoming requests to `v2` model deployment:

`kubectl replace -f https://raw.githubusercontent.com/twarik/maven/main/v2_canary.yaml`{{execute}}

Once the canary version satisfies the model behavior and performance thresholds, the deployment can be promoted to be GA to all users. The following `VirtualService` and `DestinationRule` is configured to route 100% of traffic to `v2` of our model deployment.

`kubectl replace -f https://raw.githubusercontent.com/twarik/maven/main/v2_canary100.yaml`{{execute}}

Traffic completely moved away from v1 and instead flowing into v2 of our deployment.
