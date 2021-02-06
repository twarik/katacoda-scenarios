We can now query the service at its external address

Get the external ip by:

`kubectl get svc customerchurn-service`{{execute}}

Replace the `external_ip` and run the code in the terminal.

`curl -k -v -X POST -d @input.json http://<external_ip>:8500/v1/models/customerchurn:predict`{{copy}}

This should return a set of values: `{ "predictions": [value1, value2, value13, ...] }`

Alternatively, you can query the model using the predict API

<!-- `curl -d '{"instances": [-0.57749609,  0.91324755, -0.6557859 , -0.69539349,  0.32993735, 0.80843615, -1.54035103, -1.02583358, -1.01960511, -0.99850112, 1.72572313, -0.57638802]}' -X POST http://<machine_ip>:8500/v1/models/customerchurn:predict`{{copy}} -->

`curl  -k -v -d '{"instances": [-0.57749609,  0.91324755, -0.6557859 , -0.69539349,  0.32993735, 0.80843615, -1.54035103, -1.02583358, -1.01960511, -0.99850112, 1.72572313, -0.57638802]}' -X POST http://<machine_ip>:8500/v1/models/customerchurn:predict`{{copy}}
