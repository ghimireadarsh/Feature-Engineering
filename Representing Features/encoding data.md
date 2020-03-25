### If the features values are numerical
``` python
	tf.feature_column.numeric_column('price')
	tf.feature_column.numeric_column('waitTime')
```

### If you know the keys before hand, and the features values are categorical
These features are called sparse column.
``` python

	tf.feature_column.categorical_column_with_vocabulary_list('employeeID',
			vocabulary_list = ['12345', '12123', '121234', '121', '12122']		
)
```

### If your data is already indexed i.e has integers from [0-N)
``` python

	tf.feature_column.categorical_column_with_identity('employeeID',
								num_buckets = 5
)
```

### If you don't have a vocabulary of all possible values
``` python

	tf.feature_column.categorical_column_with_hash_bucket('employeeID',
								hash_bucket_size = 500
)
```


