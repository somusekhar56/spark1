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




