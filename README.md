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



