# Benchmark Test #3

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

The tests and the training have been executed on Environment 1 and Environment 2. For each database the target environment has been specified.

#### Training Databases
The following databases has been used in the training phase. Each database has been deployed in 2 configurations of memory and CPU.
* MongoDB (Env. 1)
* MariaDB (Env. 1)
* Hypertable (Env. 1)
* CouchDB (Env. 2)
* ElasticSearch (Env. 2)

#### Test Databases
Databases expoloited in the testing phase:
* MongoDB (Env. 1)
* MariaDB (Env. 1)
* Hypertable (Env. 1)
* CouchDB (Env. 2)
* ElasticSearch (Env. 2)

#### Results
The following tables provide the weights and the computed ranking, calculated using the methodology implemented in the [Test #3 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test3/ranking_Test3.xls). The ranking is compared with the actual ranking based on the throughput values calculated during the experimental evaluation.

Parameter|Weight
--------|-------
Thrift|0
Map&Reduce|0
REST|0
Cursor|0.05851
Collection|0.11901
Companion SQL DB|0
Distributed B+ tree|0
Perfix Hash Table|0
OR-Junctions|0
AND-Junctions|0.10355
Hot Deploy|0.00696
Data Center Support|0.02025
Column Family|-0.11143
Document|0
Graph|0
Collection|0
Key Value|0.14850
Relational|-0.17495
Memtable|0
Btree|-0.10613
Hash|0.65422
Memory Cache|-0.01081
Clustering|-0.07610
Separate R/W|-0.23035
Sharding|0.00191
CPU|1.91363
Memory|-0.78428

Database|Exp. Throughput|Rank Exp|Benchmark Score|Rank Benchmark
--------|----------|------------|-----|------
MariaDB ext|5042.86   |1           |85.72 |1
MariaDB  |4759.64   |2             |85.68 |2
Hypertable FS | 1770.85  |3        |48.35 |8
Hypertable no FS |1686.06   |4     |36.40 |10
MongoDB noShard | 1381.98  |5      |40.74 |7
MongoDB Shard |1348.44   |6        |36.82 |9
postgreSQL |1339.76   |7           |18.67 |5
postgreSQL ext |1208.61   |8       |18.70 |4
CouchDB|538.24 |9                  |11.07 |12
Cassandra Shard |465.48   |10      |38.91 |6
ElasticSearch|272.39|11            |20.41 |11
Cassandra noShard |262.36   |12    |47.99 |3

