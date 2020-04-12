1. What is a common use case for where you would use tf.transform instead of a Cloud Dataflow pipeline or regular TensorFlow for preprocessing?
* __You want to invoke on-the-fly preprocessing for ML models based solely on the inputs to a model function as part of your graph__
* You want to take a rolling-average of the number of cars at an intersection during the last hour
* You need to compute the vocabulary list for categorical columns from your training dataset
* __You want to scale your inputs based on min/max value in the dataset__

________________________________________________________
2. The Analyze phase of tf.transform is carried out via:
* __A Python Beam pipeline that contains TensorFlow functions__
* A TensorFlow program that contains Beam transforms

_________________________________________________________

3. The Transform phase of tf.transform is carried out via:
* __Inside a TensorFlow serving input function during prediction__
* __Inside a Beam pipeline for evaluation and in TensorFlow during training__
* __A Beam pipeline while creating a training or evaluation dataset__
* __Inside a Beam pipeline for training and in TensorFlow during evaluation__

