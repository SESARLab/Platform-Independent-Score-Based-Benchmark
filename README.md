# A Platform-Independent Score-Based Benchmark for Distributed Databases

*Claudio A. Ardagna, Ernesto Damiani, Fulvio Frati, Davide Rebeccani*

*The business potential of big data is leading to a data-driven economy, where low-cost and low-latency data analysis
represents a major competitive advantage. The research community has proposed many technological solutions for big data, such as NoSQL databases, many of which are difficult to evaluate via standard IT procurement procedures. Lack of competences in big data domains make procurement of big data approaches a tedious and uncertain process, which might impair the success of a business.
In this paper, we address this issue by presenting a score-based benchmark for NoSQL databases, which support adopter in selecting a solution that fits their needs. The proposed benchmark is independent from the deployment platform, requires low effort on the part of end users, is extensible and can be also applied to SQL databases, can be used to evaluate databases according to different properties (e.g., performance, consistency), and can be integrated with existing benchmarks to reduce the burden of their execution. We experimentally evaluate our methodology to validate its effectiveness.*

## Experimental Settings

### Environment 1
The **experimental environment 1** consists of a physical machine Dell PowerEdge 6850 equipped with 4 Intel Xeon Quad Core 2.6 GHz, 16GB ECC RAM, 6x 146 GB Serial Attached SCSI 10K RPM, and 2x 1Gb/s Ethernet NIC. The physical machine hosts XenServer 6.2 deploying different virtual machines over which the databases target of our evaluation have been installed.

### Environment 2

### Target Databases
Target databases have been selected to cover the widest spectrum of database characteristics, the parameters supported
in the taxonomy in Figure 1, and the heterogeneity of parameter values. We note that the selected databases have
been installed with different configurations and/or within different virtual deployment environments to produce the
dataset for tuning our benchmark (training set), as well as the dataset for testing our benchmark (testing set). In
particular, we considered the following databases balancing coverage of different database architectures and popularity
of selected databases:
* *MongoDB v2.4:* NoSQL, document-oriented, schema-less database. It is composed of three main components: i) shard servers storing data; ii) configuration servers storing database configurations; iii) a router service receiving and
distributing requests to shards.
* *Cassandra v2.1.2:* NoSQL, column-based, schemaless database. It has a “masterless” architecture, where all peers (nodes) are at the same level. Cassandra supports automatic balance between nodes in the same cluster.
* *Hypertable v0.9.8.4 over Hadoop:* NoSQL, keyvalue, schema-less database. It is a massively scalable database representing data as tables of information, with rows and columns. It does not support data types, joins, and transactions.
* *PostgreSQL v9.3:* SQL, object-relational database system. It is ACID compliant, supports foreign keys, joins, views, triggers, and stored procedures. It supports most SQL:2008 data type and storage of large binary objects. PostgreSQL provides advanced features such as point in time recovery, asynchronous replication, and online/hot backups.
* *MariaDB v5.5:* SQL, object-relational database system. It is an enhanced replacement of MySQL with
more stored engines.

All databases have then been tested in different configurations varying platform-dependent parameters. Selected databases have been tested and their performance (i.e., throughput) measured using [Yahoo! Cloud Serving Benchmark] (https://github.com/brianfrankcooper/YCSB) (YCSB) framework . YCSB allows to compare the performance of different databases according to several predefined workloads, query types, and query distributions.

## Parameters

Parameters define possible architectural choices done in the configuration of a database for supporting a specific
attribute. Each `parameter` is a measurable artifact that represents an approach to support a specific attribute and
is defined as a set {l1,. . .,ln} of levels. `Levels` categorize all admissible implementations, and are defined as a pair
(name ,val), where `name` is the name of the i-th level and `val` its score.

![Parameter Taxonomy](https://github.com/altercation/solarized/raw/master/img/solarized-palette.png)

---
|Macro Area|Attribute|Parameter|
|:--------|:-------:|:-------|
|Query Type|Query API Model|Thrift|
|          |       |Map&Reduce|
|          |       |REST|
|          |       |Cursor|
|          |       |Graph|
|          |       |Collection|
|          |       |Nested hashes|
|          |       |Get-Put|
|          |Query Model|Companion SQL DB|
|          |       |Scatter/Gather local search|
|          |       |Distributed B+ Tree|
|          |       |Prefix Hash Table|
|          |       |OR-junctions|
|          |       |AND-junctions|
|DB Topology|Scalability|Hot Deploy|
|          |       |DataCenter Support|
|          |Data Model|Column-family|
|          |       |Document|
|          |       |Graph|
|          |       |Collection|
|          |       |Key-value|
|          |       |Relational|
|          |Persistency|Memtable|
|          |       |SSTable|
|          |       |SSTable on HDFS|
|          |       |BTree|
|          |       |BTree Append-only|
|          |       |Linked list|
|          |       |Linked list on disk|
|          |       |In memory|
|          |       |Hash|
|          |       |Pluggable|
|          |Versioning|Timestamp|
|          |       |Optimistic logging|
|          |       |Vector clocks|
|          |       |Multiversion storage|
|          |Partitioning|Memory caches|
|          |       |Clustering|
|          |       |Separate reads & writes|
|          |       |Sharding|
|          |Storage Layout|Row-based|
|          |       |Columnar|
|          |       |Columnar with localities|
|          |       |Log structured merge trees|
|System and Network Topology|CPU    |f(CPU) with conf_n(Q,DB,SN)|
|          |Memory|f(M) with conf_n(Q,DB,SN)|
|          |Storage|f(S) with conf_n(Q,DB,SN)|
|          |Network|f(N) with conf_n(Q,DB,SN)|
---

Each parameter can be `platform-dependent` or `platform-independent` and is initialized with the value of the selected level. A platform-dependent parameter shows a dependence on other database attributes/parameters and/or the environment where the database is deployed; a platform-independent one is generic for all databases and environments. For instance, the parameter Key-value of the attribute DataModel is platform-independent; all parameters `System and Network Topology` macro area are platform-dependent.

For each test, a subset of the parameters in the taxonomy above has been selected, relevant to the actual performance evaluation. The selection process was driven by the profile, according to an expert evaluation that identified those parameters which are likely to impact the performance of a database. Parameters are experimentally evaluated as `f(x)` with configuration `conf_i(Q_i,DB_i,SN_i)` belonging to attributes CPU and Memory. It is important to note that the more are the number of evaluated parameters `f(x) with conf i(Qi,DBi,SNi)`, the higher is the precision of our benchmark. Also, the more
detailed are database configurations `conf` (i.e., the broader is the set of parameters in Q_i, DB_i, and SN_i), the better is the precision of `f(x)`. In the extreme case in which complete configurations are available (i.e., specifying all relevant parameters in Q_i, DB_i, and SN_i), the corresponding function `f(x)` has maximum precision.

## YCSB

The [*Yahoo! Cloud Serving Benchmark (YCSB)*] (https://github.com/brianfrankcooper/YCSB) is the open source benchmarking framework used to train, test, and validate the system. YCSB consists of a workload generating client and a package of standard workloads that cover interesting parts of the performance space (read-heavy workloads, write-heavy workloads, scan workloads, etc.). YCSB is an extensible framework; it makes it easy to define new workload types, and to adapt to new data serving systems. 
