We can now query the service at its external address from our local host

If the service type is LoadBalancer, it will have its own accessible external ip.
Get the external ip by:

`kubectl get svc customer-churn-service`{{execute}}

And then send the request. Copy the statement below, replace the `machine_ip` with the external (cluster) ip address and then run the code in the terminal.

`curl -X POST -d @input.json http://<machine_ip>:8500/v1/models/customer-churn:predict`{{copy}}

This should return a set of values: `{ "predictions": [2.5, 3.0, 4.5] }`

Alternative

Query the model using the predict API

`curl -d '{"instances": [1.0, 2.0, 5.0]}' -X POST http://<machine_ip>:8500/v1/models/customer-churn:predict`{{copy}}
