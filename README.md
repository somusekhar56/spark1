# SPARK

# Hadoop Introduction: 
Hadoop is an open-source framework designed to store and process large-scale data (Big Data) efficiently using distributed computing.
# 1.1 Overview of Hadoop and Its Role in Distributed Computing

# What Hadoop Does
# Hadoop allows you to:
Store massive datasets by splitting them across multiple machines
Process data in parallel for speed
Scale easily by adding more machines
Handle failures automatically without losing data
# Key Components of Hadoop

# HDFS (Hadoop Distributed File System)
Stores large files across many nodes
Breaks data into blocks and replicates them for safety

# MapReduce
Parallel processing framework
Processes data in distributed manner

# YARN (Yet Another Resource Negotiator)
Manages cluster resources
Schedules tasks and jobs

# Hadoop Common
Shared libraries and utilities

# Role of Hadoop in Distributed Computing
Hadoop enables organizations to analyze and process:Logs, Clickstream data,Social media content, Sensor/IoT data, Structured + unstructured data.

# 1.2 Historical Context and Evolution
Hadoop was created by Doug Cutting and Mike Cafarella while working on the Nutch search engine project.
# It was inspired by Google’s two famous papers:

* 1 Google File System (GFS) – 2003
* 2  MapReduce – 2004
These papers introduced techniques for storing and processing huge datasets across clusters — Hadoop implemented these ideas in open-source form.

# Timeline of Hadoop Evolution

| Year                  | Development                                                  |
| --------------------- | ------------------------------------------------------------ |
| **2005**              | Hadoop created as part of Nutch project                      |
| **2006**              | Became a top-level Apache project                            |
| **2007–2008**         | Yahoo used Hadoop at massive scale                           |
| **2010 (Hadoop 1.x)** | Introduced HDFS + MapReduce model                            |
| **2013 (Hadoop 2.x)** | YARN introduced → better scalability                         |
| **2017–Now**          | Expansion of Hadoop ecosystem (Hive, Pig, Spark, HBase etc.) |

# Why Hadoop Became Popular
Hadoop became essential because: Data volume grew enormously,Traditional databases couldn't handle large/fast/varied data,Hadoop provided a cheap, scalable, reliable solution
Easy to add nodes and grow cluster size.

# Modern Hadoop Ecosystem
Hadoop is not just HDFS + MapReduce anymore.
It includes tools like:

Hive → SQL on Hadoop

Pig → Scripting

Spark → Fast in-memory processing

HBase → NoSQL database

Sqoop / Flume → Data ingestion

Oozie → Workflow scheduling

# 2. Spark Introduction
Apache Spark is an open-source, fast, in-memory data processing engine used for big data processing and analytics.

# 2.1 Key Features / Advantages of Apache Spark 
1. In-Memory Processing (Very Fast)  -  Spark stores data in memory (RAM), making processing 100x faster than Hadoop MapReduce.
2. Supports Multiple Workloads - Batch processing, Real-time streaming (Spark Streaming), Machine learning (MLlib),Graph processing (GraphX),SQL queries (Spark SQL)
3.  Easy to Use - Spark provides simple APIs in Python, Scala, Java, R. PySpark is especially popular for data engineering.
4.  Fault Tolerant - Uses RDD (Resilient Distributed Dataset) which provides fault tolerance using lineage information.
5.  Works with Hadoop - Spark can run on top of:  HDFS,YARN,Hadoop clusters,Standalone cluster,Cloud (AWS, Azure, GCP)
6.  Lazy Evaluation - Execution happens only when required → improves performance.
7.  Distributed Computing - Spark automatically distributes data and computation across multiple nodes in a cluster.
   
#   2.2 Comparison: Apache Spark vs Hadoop MapReduce
| Feature             | Apache Spark                | Hadoop MapReduce       |
| ------------------- | --------------------------- | ---------------------- |
| **Speed**           | Very fast (in-memory)       | Slow (disk-based)      |
| **Processing**      | Real-time + batch           | Only batch             |
| **Data Storage**    | Uses RAM                    | Uses disk (HDFS)       |
| **Ease of Use**     | Easy (APIs in Python/Scala) | Harder, verbose code   |
| **Use Cases**       | Streaming, ML, SQL, graphs  | Simple batch jobs      |
| **Fault Tolerance** | RDD lineage                 | Replication in HDFS    |
| **Performance**     | 10–100x faster              | Slower due to disk I/O |

# 3. Spark Architecture Overview

Apache Spark follows a master–slave cluster architecture that distributes data and computation across multiple machines.
Spark’s architecture is designed for high-speed, in-memory processing and supports various workloads like SQL, ML, streaming, and graphs.

# 3.1 Key Components of Spark Architecture
Key Components of Spark Architecture Spark follows a master-slave distributed architecture with the following components:

# 1 Driver Program
The driver is the starting point of a Spark application.
It runs the user code (your Python/Scala program).
Converts code into tasks
Sends tasks to executors

# 2. Cluster Manager
It manages the resources of the cluster. Spark supports:
* Standalone Cluster Manager
* YARN (Hadoop)
* Mesos
* Kubernetes
Cluster Manager allocates executors to the driver program.

# 3. Executors
* Executors are worker processes running on cluster nodes.
* Execute tasks assigned by the driver
* Store data in memory for caching
* Send results back to the driver

 #  4 Workers
Nodes that run executors

# 5 RDD (Resilient Distributed Dataset)
Fundamental data structure in Spark

Immutable, distributed data collection

# Driver program in DAG
# 1. DAG (Directed Acyclic Graph)
Spark converts your code into a logical execution plan (DAG).
This DAG is optimized into stages.
# 2.DAG Scheduler
Converts DAG into stages
Creates tasks for each stage

# 3.2 Interaction Between Components During Execution
Here is the step-by-step workflow of how Spark components interact during code execution.

# Submit Application
* User submits Spark code
* Driver begins execution

# Driver Program Starts
Creates and start SparkSession,SparkContext
Communicates with Cluster Manager

# Driver converts your code → DAG
Logical plan → optimized plan → DAG of stages.

# Driver requests executors from Cluster Manager
Cluster Manager allocates:
* CPU cores
* Memory
* Executors on worker nodes
  
 # Driver sends tasks to Executors
Tasks correspond to partitions of the data.

# Executors run the tasks
Executors:
Read data
Perform computation (map, reduce, filter, join)
Store intermediate results in memory
Use caching if required

# Executors return results
Executors send results back to the driver.
If it is an action like:
count()
collect()
show()
The driver displays the output.

# Executors continue until the job ends
When the job finishes:
Executors shut down
Resources are released

# Spark Components
#  Driver
Driver is the master process in Spark. It creates the SparkContext, builds the job execution plan, and coordinates all the worker nodes.

# Key responsibilities of Driver:
Runs the main() function of the application.
Creates the SparkContext / SparkSession.
Builds the DAG (Directed Acyclic Graph).
Divides the job into stages and tasks.
Communicates with the cluster manager.
Collects results after execution.

# Executors
Executors are worker processes that run tasks and store data. They perform the actual computations in Spark

# Each executor:
Executes tasks sent by the driver.
Stores data in memory (for caching in RDD/DataFrame).
Reports the status back to the driver.

# Responsibilities:
Runs tasks in parallel.
Holds RDD/DataFrame partition data.
Performs calculations, shuffling, and data storage.
Provides fault tolerance by recomputing lost partitions.

# Cluster Manager
Cluster Manager allocates resources and starts Executors and managing nodes in the cluster.Spark supports Standalone, YARN, Mesos, and Kubernetes as cluster managers.

# Responsibilities:
Allocates CPU and memory to executors.
Launches executors on worker nodes.
Monitors executors and nodes.

# Difference between all three failures (Driver vs Executor vs Cluster Manager)(important for interview)
# Driver Failure
If the driver fails, the entire Spark application fails. Since the driver manages the DAG, task scheduling, and coordinates all executors, Spark cannot continue execution. The job must be restarted.

# Executor Failure
If an executor fails, Spark detects it and the cluster manager launches a new executor. The tasks running on that executor are rescheduled and re-executed on other executors. The job continues normally due to Spark’s fault tolerance and lineage.

# Culster manager failure
If the cluster manager fails, the impact depends on HA. With High Availability, a standby cluster manager takes over and the job continues normally. Without HA, the cluster cannot allocate new resources, no new executors can start, and running jobs may eventually fail.

High Availability ensures that if the master component (cluster manager) goes down, a standby master immediately takes over so the Spark application and cluster continue to run smoothly.

Cluster Managers that support HA:
YARN – ResourceManager HA

Standalone Mode – Master HA

Mesos – Master HA

Kubernetes – Control plane HA

# 5. Core Concepts in Apache Spark

# 5.1 RDD (Resilient Distributed Dataset)

RDD is the fundamental data structure of Spark.Immutable,(once created object we cant change) distributed data collection.Fault-tolerant distributed data structure

# Key Features
* Resilient → Automatically recovers from failures
  
* Distributed → Data is split across multiple cluster nodes
  
* Immutable → Once created, it cannot be changed
  
* Lazy Evaluation → Execution happens only when an action is performed
  
* In-memory processing → Fast data computation

# Used for
Unstructured data(no schema)

Complex transformations

Low-level operations

Fault-tolerant processing

# What are the two types of RDD operations?
1 Transformations → return new RDD
Example: map, filter, flatMap, reduceByKey

2 Actions → return result
Example: collect, count, take, saveAsTextFile


# 5.2 Spark Core
Spark Core is the foundation layer of the entire Spark architecture.
# It provides:
Memory management

Fault tolerance

Task scheduling

RDD operations

Communication with cluster manager

# Why Spark Core is important
All other modules (SQL, Streaming, MLlib, GraphX) are built on top of Spark Core.

# 5.3 Spark SQL
Spark SQL is the module for structured and semi-structured data.
# Supports:
SQL queries

DataFrames

Datasets

Hive integration
# Advantages
Easy to write SQL-like queries

Optimized by Catalyst Optimizer

Fast execution using Tungsten engine

Works with multiple data sources (Hive, Parquet, JSON, CSV, etc.)

# What is the Catalyst Optimizer?
A query optimization engine in Spark SQL that automatically:
Optimizes logical plans
Optimizes physical plans
Applies rule-based transformations
Improves performance

# 5.4 Spark Streaming
Spark Streaming provides real-time data processing.
Example sources:Kafka,Flume,Socket,Files
# How it works
Data is divided into small time intervals called micro-batches.
# Use cases
Streaming logs

IoT sensor data

Real-time dashboards

Fraud detection
# Types:
DStreams (Older API)
Structured Streaming (Newer, faster, recommended)

# 5.5 MLlib (Machine Learning Library)
MLlib is Spark's built-in machine learning library.
# Provides algorithms for:
Classification

Regression

Clustering

Recommendation

Dimensionality reduction
# Also includes:
Feature extraction

Pipelines

Model evaluation
# Why MLlib?
Distributed ML processing

Very fast on large datasets

Scales horizontally across cluster

# 5.6 GraphX
GraphX is used for graph processing and graph-parallel computations.
#  Used for:
Social network analysis

PageRank

Graph traversal

Link analysis
# Features
Use RDDs to represent graphs

Comes with optimized graph operators

# 6. RDD, Dataframe, Dataset [Difference and Converting from one to Another]: 

# 6.1 Differences Between RDD, Dataframe, and Dataset: Understanding the distinctions between these abstractions. 

# DataFrame
DataFrame is a distributed table with schema, optimized by Catalyst. It is faster and preferred for structured data.
# Use DataFrame when:
* You want performance
* You want SQL-like processing

# Dataset (Scala & Java only)
Dataset combines the advantages of RDD (type safety) and DataFrame (optimization). Available only in Scala/Java.
# Performance Ranking:
DataFrame ≈ Dataset > RDD



