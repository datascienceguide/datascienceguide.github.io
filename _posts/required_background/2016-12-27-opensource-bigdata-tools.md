---
layout: post
title:  "Big Data Tools"
categories:  big-data 
---

## Popular Hadoop Projects

__Hadoop__: A distributed file system and MapReduce engine YARN.

__Spark__: An in-memory based alternative to Hadoop's MapReduce which is better for machine learning algorithms. 

Spark SQL, MLlib (machine learning), GraphX (graph-parallel computation), and Spark Streaming.

__Storm__: Distributed tool for processing fast, large streams of data.

__Cassandra__: NoSQL system implemented on Hadoop.

__Hive__: Allows users to create SQL-like queries (HQL) and convert them to MapReduce.

__HCatalog__: A centralized metadata management and sharing service for Hadoop, allowing a unified view of all data in Hadoop clusters.

__Pig__: An easy to learn hadoop-based language that is adept at very deep, very long data pipelines.

__Mahout__: A data mining library using the most popular data mining algorithms using the Map Reduce model.

## Non-Hadoop Projects  
__NoSQL (Not Only SQL)__: A database that is not based storage and retrieval of tabular relations used in relational databases. Some can provide a distributed database.  

__Examples__: MongoDB, CouchDB, Accumulo, and some NoSQL databases are implemented on Hadoop: Cassandra, HBase.

__SQL__: Can spill to disk allowing datasets to be larger than memory size.  

__MADlib__: Machine learning library extension for PostgreSQL.

## Hadoop Ecosystem
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools_last.png)

+ The blue is the necessary components of a Hadoop Ecosystem
+ Some tools provide several functionalities.
+  i.e. Hadoop is a distributed file system with MapReduce engine and scheduler.

### Distributed File System
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-dfs.png)

__HDFS (Hadoop Distributed File System)__ is a distributed file-system across multiple interconnected computer systems (nodes).

+ Data is stored across multiple hard drives.

__Lustre__: DFS used by most enterprise High Performance Clusters (HPC). Usually uses a shared networked drive.

__Google File System (GFS)__: Google propriety distributed file system.

__MapR__: DFS inspired by HDFS but written in C++ instead of Java. 

### MapReduce
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-MapReduce.png)

+ MapReduce is the engine that processes data in a Hadoop Ecosystem.
+ Spark and Tez uses a more flexiable in memory model of MapReduce which is better for Machine Learning algorithms.

### Scheduler
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-Scheduler.png)

In order for multiple people to run on the same cluster, a scheduler is needed.

### Data Manipulation
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-Data-Manipulation.png)

These are the tools to help parse, transform, and combine various datasets.

+ Hive, Spark SQL, Impala, Cassandra, and HBase all use a SQL-like language to help manipulate data.
+ Hive can be implemented using the Spark MapReduce Engine (significantly speeding it it's processes).

### Data Analysis
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-ML_algorithms.png)

There are several Machine Learning algorithms already in place for the Hadoop Ecosystem.

+ Mahout can be implemented on Spark, Tez, and Hadoop
+ Spark also has GraphX, which uses graphs to perform analytics (PageRank, etc.)

There is also specialized tools:

__Hadoop Image Processing Interface (HIPI)__: Image processing package helping to determine image similarity.

__SpatialHadoop__: Extension to process datasets of spatial data in Hadoop.

### Serialization
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-serialization.png)

Parsing, transforming and combining the data into a useable dataset can be time consuming. Thus, once a suitable amount of work is done to create a useable dataset it is best to save it for future work. 

Serialization saves the state of the data, allowing it to be recreated at a later date.

+ JAVA Serialization is the worst of the above and should only be used for legacy reasons

__Avro:__ Serialization made for Hadoop.

__JSON:__ Java Script Object Notation is a convenient way of describing, serializing, and transferring data.

__Protocol Buffers:__ More optimal serialization that requires the precise structure of the data when job is being run. Has less support for programming languages.

__Parquet:__ A columnar data storage format, allowing it perform well for structured data with a fair amount of repetition.

### Data Transfer
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-Data_transfer.png)

Data transfer of large amounts of data to and from dfs.

__Flume, DistCp__: Move files and flat text into Hadoop.

__Sqoop__: Move data between Hadoop and SQL.

### Streaming
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-Streaming.png)

__Streaming__ provides new calculations based on incoming data.

__Example__: Netflix 'Trending Now' feature. 
Possibly with personalized medicine to use medical devices to detect heart attacks before they happen.

__Spark Streaming__: Uses a micro-batch model that checks updates every 0.5-10 seconds and updates it's model.

__Storm__: Uses either streaming or micro-batch updates to update model.

### Management and Monitoring
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-management.png)

__Node configuration management__: Puppet, Chef. Change operating system parameters and install software.

__Resource Tracking__: Monitor the performance of many tools.

__Coordination__: Helps synchronize many tools in a single application: Zookeeper.

---

__Ambari__: Tool to help install, starting, stopping, and reconfiguring Hadoop cluster.

__HCatalog__: Central catalog of file formats and locations of data. Data looks like a table-like to user. 

__Nagios__: Alert failures and problems through a graphical interface and alert administration though email of problems.

__Puppet, Chef__: Manager for configuration of a large number of machines.

__Zookeeper__: Helps coordination of tools.

__Oozie__: Workflow scheduler to start, stop, suspend and restart jobs, controlling the workflow so that no task is performed before it is ready.

__Ganglia__: Visualize how systems are being used and keeping track of general health of cluster.

### Security, Access Control, and Auditing
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-security.png)

Hadoop in itself doesn't provide much security. As Hadoop increased in popularity, so has security projects.

Kerberos, Sentry, Knox are such projects.

### Cloud Computing and Virtualization
![alt text](https://raw.githubusercontent.com/NormallySane/Big_Data_Presentation/master//images/Big-data_tools-Cloud.png)

Sometimes you only need intermediate use of a cluster and creating/maintaining one of your own is prohibitively expensive. 

Cloud computing and virtualization tools provide easy construction of Hadoop environments with relative ease on cloud computering environments like [AWS](http://aws.amazon.com/).

### Distribution Platforms

Distribution platforms help (for a cost) easy installation and software maintaince of a Hadoop cluster. 

+ Tool versions are checked for compatability, usually meaning that they are not the newest versions

Some of these are: [Cloudera](http://www.cloudera.com/content/cloudera/en/home.html), [MapR](https://www.mapr.com/), and [Hortonworks](http://hortonworks.com/).


# Next Steps: Data Science Framework

Now that you have been introduced to the tools, start on the next module and learn the [data science framework](data-science-framework/).
