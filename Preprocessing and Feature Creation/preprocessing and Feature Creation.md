__1. Getting started with preprocessing Feature Creation__
__2. Use Apache Beam and Cloud Data Flow for feature Engineering__

### Feature Engineerring often requires global statistics and vocabularies
``` python
	features['scaled_price'] = (features['price'] - min_price) / (max_price - min_price)

```

```python
		tf.feature_column.categorical_column_with_vocabulary_list('city',
			keys=['San Diego', 'Los Angeles', 'San Francisco', 'Sacramento'])
```

### Things that are commonly done in preprocessing
__In BigQuery or Beam__
1. Remove examples that you don't want to train on
2. Compute vocabularies for categorical columns
3. Comptue aggregate statistics for numeric columns
4. Compute time-windowed statistics (e.g. number of producs sold in previous hour) for use as input features

__In Tensorflow or Beam__
1. Scaling, discretization, etc of numeric features
2. Splitting, lower-casing, etc. of textual features
3. Resizing of input images
4. Normalizing volume level of input audio


#### Example of preprocessing in BigQuery
``` SQL
	SELECT
		(tolls_amount + fare_amount) AS fare_amount,
		DAYOFWEEK(pickup_datetime) AS dayofweek,
		HOUR(pickup_datetime) AS hourofday,
		....
	FROM
		'nyc-tlc.yellow.trips'
	WHERE
		trip_distance > 0;
```

#### There are two places for feature creation in TensorFlow
1. Features are preprocessed in input_fn(train, eval, serving)
``` python
	features['capped_rooms'] = tf.clip_by_value(
				features['rooms'],
				clip_value_min = 0,
				clip_value_max = 4
)

2. Features columns are passed into the estimator during construction
``` python
	lat = tf.feature_column.numeric_column('latitude')
	dlat = tf.feature_column.bucketized_column(lat, boundaries=np.arange(32,42, 1).tolist())
```

#### Examples of preprocessing in Tensorflow input_fn
``` python
	def add_engineered(features):
		lat1 = features['pickuplat']
		...
		dist = tf.sqrt(latdiff*latdiff + londiff*londiff)
		features['euclidean'] = dist
		return features
```
_How do we make sure that this function gets called during both training and prediction?_


#### Wrap features to call to the feature engineering to function
__Wrap features in training/evaluation input function__
``` python
	def input_fn():
		features = .....
		label = .......
		return add_engineered(features), label
```

__Wrap features in serving input function also__
``` python
	def serving_input_fn():
		feature_placeholders = ...
		features = ...
		return tf.estimator.export.ServingInputReceiver(
				add_engineered(features), feature_placeholders			
			)
```

#### Example of preprocessing via feature columns
``` python
	def build_estimator(model_dir, nbuckets):
		latbuckets = np.linspace(38.0, 42.0, nbuckets).tolist()
		b_plat = tf.feature_column.bucketized_column(plat, latbuckets)
		b_dlat = tf.feature_column.bucketized_column(dlat, latbuckets)

		return tf.estimator.LinearRegressor(
			model_dir = model_dir,
			feature_columns = [..., b_plat, b_dplat, ...]			
			) 
```

### Example of preprocessing in Beam 
``` python

	def to_csv(rowdict):
		if distance(rowdict['pickuplon'], ...) > 10 # only rides more than 10 km
			CSV_COLUMNS = 'fare_amount, dayofweek, ..., key'.split(',')
			yield ','.join([str(rowdict[k] for k in CSV_COLUMNS)])
	
	def preprocess():
		...
		for n, step in enumerate(['train', 'valid']):
			(p | 'read_{}'.format(step) >>
				 beam.io.Read(beam.io.BigQuerySource(query=query))
			  | 'tocsv_{}'.format(step) >> beam.FlatMap(to_csv)

			  | 'write_{}'.format(step) >> beam.io.Write(beam.io.WriteToText(outfile))
			)
		p.run()


```
