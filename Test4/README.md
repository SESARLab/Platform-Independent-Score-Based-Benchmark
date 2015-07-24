# Benchmark Test #4

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

The tests and the training have been executed on Environment 2. For each database the target environment has been specified.

#### Training Databases
Databases used in the training phase:
* MongoDB 
* MariaDB 
* Hypertable 
* CouchDB 
* ElasticSearch

#### Test Databases
Databases exploited in the testing phase:
* MongoDB
* MariaDB
* Hypertable 
* CouchDB 
* ElasticSearch 

#### Results
The following tables provide the weights and the computed ranking, calculated using the methodology implemented in the [Test #4 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test4/ranking_Test4.xls). The ranking is compared with the actual ranking based on the throughput values calculated during the experimental evaluation.

Parameter|Weight
--------|-------
Thrift|0
Map&Reduce|0
REST|0
Cursor|0
Collection|0
Companion SQL DB|0
Distributed B+ tree|0
Perfix Hash Table|0
OR-Junctions|0
AND-Junctions|0
Hot Deploy|0
Data Center Support|0
Column Family|0
Document|0
Graph|0
Collection|0
Key Value|0
Relational|0
Memtable|0
Btree|0
Hash|0
Memory Cache|0
Clustering|0
Separate R/W|0
Sharding|0
CPU|0
Memory|0

Database|Exp. Throughput|Rank Exp|Benchmark Score|Rank Benchmark
--------|----------|------------|-----|------

