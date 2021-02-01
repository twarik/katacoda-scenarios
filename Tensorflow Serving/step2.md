For this scenario we will deploy the Tensorflow **customer churn** model trained on the notebook server, and exported to a SavedModel(servable) format which we can run with TF serving.

To get this model, We clone the Maven repo.

`git clone https://github.com/twarik/maven`{{execute}}

Set path to the location of demo models.
`model_dir=/root/maven/saved_model_customer_churn`{{execute}}
