1. Which of these accurately describes the relationship between Apache Beam and Cloud Dataflow?
* They are the same
* Cloud Dataflow is the API for data pipeline building in java or python and Apache Beam is the implementation and execution framework.
* Cloud Dataflow is the proprietary version of the Apache Beam API and the two are not compatible
* __Apache Beam is the API for data pipeline building in java or python and Cloud Dataflow is the implementation and execution framework.__



2. TRUE or FALSE: The Filter method can be carried out in parallel and autoscaled by the execution framework:
* True
* __False__

3. What is the purpose of a Cloud Dataflow connector?

``` python
	.apply(TextIO.write().to(“gs://…”));
```

* __Connectors allow you to output the results of a pipeline to a specific data sink like Bigtable, Google Cloud Storage, flat file, BigQuery, and more...__
* Connectors allow you to chain multiple data-processing steps together automatically so they process in parallel
* Connectors allow you to authenticate your pipeline as specific users who may have greater access to datasets


4. Below you'll find a Cloud Dataflow preprocessing graph. Correctly identify the terms for A, B, and C.
* 
1. __A is a data source,__
2. __B are transformation steps, and__
3. __C is a data sink__

* 
1. A is a data stream,
2. B are transformation steps, and
3. C is a data source

* 
1. A is a data stream,
2. B are transformation steps, and
3. C is a data sink

5. To run a pipeline you need something called a ________
* executor
* pipeline
* Apache Beam
* __runner__

6. Your development team is about to execute this code block. What is your team about to do?
``` python
	mvn compile -e exec:java \
		-Dexec.mainClass=$MAIN \
		-Dexec.args='--project=$PROJECT' \
		--stagingLocation=gs://$BUCKET/staging/ \
		--tempLocation=gs://$BUCKET/staging/ \
		--runner="DataflowRunner"

```

* __We are compiling our Cloud Dataflow pipeline written in Java and are submitting it to the cloud for execution__
* We are compiling our Cloud Dataflow pipeline written in Python and are loading the outputs of the executed pipeline inside of Google Cloud Storage (gs://)
* We are preparing a staging area in Google Cloud Storage for the output of our Cloud Dataflow pipeline and will be submitting our BigQuery job with a later command

7. TRUE or FALSE: A ParDo acts on all items at once (like a Map in MapReduce)
* True
* __False__








