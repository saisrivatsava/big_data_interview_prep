
## YARN architecture

* YARN provides its core services via two types of long-running daemon: **a resource manager (one per cluster)** to manage the use of resources across the cluster, and **node managers** running on all the nodes in the cluster to launch and monitor containers.

* A Container executes an application-specific process with a constrained set of resources (memory, CPU, and so on).

![alt text](https://github.com/saisrivatsava/big_data_interview_prep/blob/main/image.png)

## Hadoop Interview Questions

* https://www.simplilearn.com/tutorials/hadoop-tutorial/hadoop-interview-questions


## Hadoop Small File Problem.

* A file which is less than HDFS block size (64MB/128MB) is termed as small file.
NameNode stores all files metadata in memory, so if you are storing lots of small files, NameNode has to maintain its metadata, for a file metadata, it occupies 150 bytes so in the case of million files it would cost around 3GB of memory. So, a large number of small files will end up using a lot of memory of the master and scaling up in this fashion is not feasible. When there are large number of files, there will be a lot of seeks on the disk as frequent hopping from data node to data node will be done and hence increasing the file read/write time.

* Small File problem in MapReduce: In MapReduce, Map task process a block of data at a time. Many small files mean lots of blocks – which means lots of tasks, and lots of book keeping by Application Master. This will slow the overall cluster performance compared to large files processing.

* In order to resolve small file problem we can group the files in a larger file and for that, we can use HDFS's sncy() or write a program or we can use below methods:

1) HAR files: It builds a layer system on top of HDFS. HAR command will create a HAR file which then runs a MapReduce job to avoid the files being archived into the small number of HDFS files.

2) HBase: It is a type of storage which creates larger files depending on the access pattern of small files.

3) Sequence File: Here we use the filename as key and content as value. We write a program to put lots of small files in a single Sequence File. They are splittable and so MapReduce can operate each chunk independently and in parallel.

4) Filecrush tool: It will turn many small files into fewer larger files. It also changes from text to sequence.


