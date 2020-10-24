## Spark Applications and Architecture

* Spark Applications consist of a **driver process** and a set of **executor processes**. 
* ### Driver Process:
* The driver process runs your main() function, sits on a node in the cluster, and is responsible for three things:

* maintaining information about the Spark Application;

* responding to a user’s program or input;

* Analyzing, distributing, and scheduling work across the executors (discussed momentarily).

* The driver process is absolutely essential—it’s the heart of a Spark Application and maintains all
relevant information during the lifetime of the application


## Hive with Spark 

* https://spark.apache.org/docs/latest/sql-data-sources-hive-tables.html

## Spark Jobs, Stages and Tasks

### Jobs

* Invoking an action inside a Spark application triggers the launch of a Spark job to fulfill it.
To decide what this job looks like, Spark examines the graph of RDDs on which that action depends and formulates an execution plan.

### Stages

* A Stage is a sequence of Tasks that don't require a Shuffle in-between.

* A stage corresponds to a collection of tasks that all execute the same code, each on a different subset of the data. 
Each stage contains a sequence of transformations that can be completed without shuffling the full data.

### Tasks

* A Task is a single operation (.map or .filter) applied to a single Partition.

* Each Task is executed as a single thread in an Executor!

* If your dataset has 2 Partitions, an operation such as a filter() will trigger 2 Tasks, one for each Partition.
