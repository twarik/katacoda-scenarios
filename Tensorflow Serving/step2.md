For this scenario we will deploy the Tensorflow **customer churn** model trained on the notebook server, and exported to a SavedModel(servable) format which we can run with TF serving.

We retrieve the SavedModel model from a repo.

```
mkdir -p ~/root/saved_model_customer_churn

wget -qO- https://github.com/twarik/maven/blob/main/saved_model_customer_churn/1.zip?raw=true | bsdtar -xvf- -C ~/root/saved_model_customer_churn
```{{execute}}
