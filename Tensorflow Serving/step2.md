To export and save a model as TensorFlow servable.

```python
import tensorflow as tf
tf.saved_model.save(model,
                    export_dir="./saved_model_name",
                    signatures=None
)
```

For this scenario we will deploy a pretrained saved model from Tensorflow/models. We will use a toy model called **Half plus two** which generates  **`0.5*x+2`** for the values of **`x`** we provide for prediction:

To get this model, first clone the TensorFlow Serving repo.

<!-- `git clone https://github.com/tensorflow/serving`{{execute}} -->
`git clone https://github.com/twarik/maven`{{execute}}

Set path to the location of demo models.

<!-- `model_dir=/root/serving/tensorflow_serving/servables/tensorflow/testdata/saved_model_half_plus_two_cpu`{{execute}} -->

`model_dir=/root/maven/saved_model_customer_churn`{{execute}}

## Create ConfigMaps from directories

```
# Create the local directory
mkdir -p /var/config/

# Download the sample files into `/var/config/` directory
wget https://kubernetes.io/examples/configmap/game.properties -O /var/config/game.properties
wget https://kubernetes.io/examples/configmap/ui.properties -O /var/config/ui.properties

# Create the configmap
kubectl create configmap customer-churn-v1-config --from-file=/var/config/
```{{execute}}
