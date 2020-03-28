Beam is a way to write elastic data processing pipelines


##### This simple line of code analyzes the number of words in a text document.
``` python

	p = beam.Pipeline()
	(p 				# Open source API (Apache Beam) executed on Flink, Spark, etc.
		| beam.io.ReadFromText('gs://...')
		| beam.Map(Transform)  # Parallel tasks (autoscaled by execution framework)
		| beam.GroupByKey()
		| beam.FlatMap(Filter)
		| beam.io.WriteToText('gs://...')
	)
	p.run();

```

``` python

	def Transform(line):
		return (count_words(line), 1)
	
	def Filter(key, values):
		return key>10
```

The code is same between real-time or streaming data and batch
``` python

	p = beam.Pipeline()
	(p 				# Open source API (Apache Beam) executed on Flink, Spark, etc.
		| beam.io.ReadStringsFromPubSub('project/topic')
		| beam.WindowInto(SlidingWindows(60))
		| beam.Map(Transform)  # Parallel tasks (autoscaled by execution framework)
		| beam.GroupByKey()
		| beam.FlatMap(Filter)
		| beam.io.WriteToText('table')
	)
	p.run();

```

### BigQuery --> Cloud Dataflow--> Cloud Storage ===> Together they form a pipeline


### Dataflow terms and concepts
The Pipeline is executed on the cloud by a Runner; each step is elastically scaled

``` python
	def packageHelp(record, keyword):
		count = 0
		package_name=''
		if record is not None:
			lines=record.split('\n')
			for line in lines:
				if line.startswith(keyword):
					package_name=line
				if 'FIXME' in line or 'TODO' in line:
					count+=1
			packages = (getPackages(package_name))
		for p in packages:
			yield(p, count)
```	

### A pipeline is a directed graph of steps
Read in data, transform it, write out

Can branch, merge, use if-then statements, etc.

Python Syntax
``` python
	import apache_beam as beam
	if __name__ == 'main':
		# Crate a pipeline paramterized by commandline flags
		p = beam.Pipeline(argv=sys.argv)

		(p
			| 'Read' >> beam.io.ReadFromText('gs://...') # read input
			| 'CountWords' >> beam.FlatMap(lambda line: count_words(line))
			| 'Write' >> beam.io.WriteToText('gs://...') # write output
		
		)
		p.run(); # run the pipeline

```

### Executing Pipeline (Python)
Simply running main() runs pipeline locally

``` python
	python ./grep.py
```

To run on cloud specify cloud parameters and submit the job to Dataflow

``` python
	python ./grep.py \
		--project=$PROJECT \
		--job_name=myjob \
		--staging_location=gs://$BUCKET/staging/ \
		--temp_location = gs://$BUCKET/staging/ \
		--runner=DataflowRunner
```
