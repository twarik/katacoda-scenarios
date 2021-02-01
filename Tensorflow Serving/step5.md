Say, we want to deploy a new TensorFlow model version  serving binary. Making changes to model deployments should always be done in an iterative way such that the new model behavior and performance can be properly tested, validated before being promoted as GA to all clients .

1. Apply the deployment to the cluster:

`kubectl apply -f https://raw.githubusercontent.com/twarik/maven/main/resources_2.yaml`{{execute}}

3. Update the traffic weight **(Setup V2 Canary Routing)**

Now that we have our new model deployment, we would like to gradually roll it out to a subset of the users.
This can be done by updating our `VirtualService` to route a small % of traffic to `v2` subset.

We will be cautious and update our VirtualService to route 30% of incoming requests to v2 model deployment:

`kubectl replace -f v2_canary.yaml`{{execute}}
