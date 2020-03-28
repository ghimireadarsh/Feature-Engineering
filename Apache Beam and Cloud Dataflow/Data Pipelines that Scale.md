### MapReduce approach splits Big Data so that each compute node processes data local to it

Apache Beam and Data Flow are build on the implementation of the mapreduce framwork

#### Map 
1. should be a stateless function so that it can ve scheduled to run in parallel across the nodes in the cluster
2. Each map reads the data from the storage ont he node wheere this running, processes the data and generates an output.
3. The output of the map operations are shuffled from the different nodes in the cluster to the next stage of processing called Reduce.

#### Reduce
1. Can think of reduce operation as affregation operation over data.
2. The aggregation can be operations like counting numbers of data elements or computing sums.
3. Once the reduced operations are finished the result becomes the output of the MapReduce step in a Pipeline.


If you want to take a transformation in your data processing pipeline and let data flow run it at scale with automatic distribution across many nodes in a cluster. Then you should use the Apache beams __ParDo class__. 

#### ParDo

ParDo acts on one item at a time (Like a Map in MapReduce)

1. Is short for parallel do. 
2. The transformation steps created using ParDo or similar to the maps in MapReduce
3. The transformations used with ParDo, have to be stateless so they can be run in parallel.

Multiple instances of class on many machines

Should not contain any state


Useful for :
* Filtering (choosing which inputs to emit)
* Extracting parts of an input (e.g. Fields of Tensorflow)
* Converting one Java type to another
* Calculating calues from different parts of inputs.

This is somewhat restrictive but useful for many tasks. 

For example: 

You're building a data processing pipeline and analyzing web server files and you may need to filter out the log entries that include IP address of a visitor to your website. 

You can do that with a stateless transformation or if you want to extract the value of the IP address from the string of the log entry, you can do that statelessly. 

Other stateless processing operations like converting strings through integers or any calculations that work was just a part of the input, like a raw of data are all good candidates for a ParDo.


### Python : Map vs FlatMap

Use map for 1 to 1 relationship between input and output
``` python
	'WordLengths' >> beam.Map(lambda word: (word, len(word)))

```

FlatMap for non 1 to 1 relationships, usually with generator
``` python
def vowels(word):
	for ch in word:
		if ch in ['a','e','i','o','u']:
			yeild ch
'WordVowels' >> beam.FlatMap(lambda word : vowels(word))

```

Java : Use apply(ParDo) for both cases


### GroupBy Operation is akin to shuffle

In Dataflow, shuffle explicitly with a GroupByKey

Create a key-value pair in ParDo

Then group by the key

``` python

	cityAndZipcodes = p 
			| beam.Map(lambda address: (address[1], address[3]))
			| beam.GroupByKey()

```

### Combine.PerKey lets you aggregate

Can be applied to a PCollection of values:
``` python 
	totalAmount = salesAmounts | Combine.globally(sum)
```

And also to a grouped Key-Value Pair :
``` python
	totalSalesPerPerson = salesRecords | Combine.perKey(sum)
```

Many buil-in functions : Sum, Mean etc.


