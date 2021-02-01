For this scenario we will deploy the **customer churn** model trained on the notebook server. We will then export the Tensorflow model to a SavedModel(servable) format which we can run with TF serving.

To export and save a model as TensorFlow servable.

```python
import tensorflow as tf
tf.saved_model.save(model,
                    export_dir="./saved_model_name",
                    signatures=None
)
```

To get the customer churn servable model, We clone the Maven repo.

`git clone https://github.com/twarik/maven`{{execute}}

Set path to the location of demo models.
`model_dir=/root/maven/saved_model_customer_churn`{{execute}}
