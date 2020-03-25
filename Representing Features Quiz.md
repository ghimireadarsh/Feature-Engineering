1. What is one-hot encoding?
* __One hot encoding is a process by which categorical variables are converted into a form that could be provided to neural networks to do a better job in prediction.__
* One hot encoding is a process by which only the hottest numeric variable is retained for use by the neural network.
* One hot encoding is a process by which numeric variables are converted into a categorical form that could be provided to neural networks to do a better job in prediction.
* One hot encoding is a process by which numeric variables are converted into a form that could be provided to neural networks to do a better job in prediction.
_________________________________________________________________________________________

2. Which of these offers the best way to encode categorical data that is already indexed, i.e. has integers in [0-N]?
* Ans :
``` python 
		tf.feature_column.categorical_column_with_identity
```
* 
```python
		tf.feature_column.categorical_column_with_vocabulary_list
```
* 
```python
		tf.feature_column.categorical_column_with_hash_bucket
```
______________________________________________________________________________________________

3. What do you use the tf.feature_column.bucketized_column function for?
* __To discretize floating point values into a smaller number of categorical bins__
* To count the number of unique buckets the input values falls into
* To compute the hash buckets needed to one-hot encode categorical values

