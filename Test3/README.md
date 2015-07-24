# Benchmark Test #3

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

The tests and the training have been executed on Environment 1 and Environment 2. For each database the target environment has been specified.

#### Training Databases
Databases used in the training phase:
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
Thrift|-0.09851
Map&Reduce|0
REST|0
Cursor|0.04291
Collection|-0.21754
Companion SQL DB|0
Distributed B+ tree|0
Perfix Hash Table|0
OR-Junctions|-0.04356
AND-Junctions|0
Hot Deploy|-0.05666
Data Center Support|-0.01183
Column Family|0.10437
Document|0
Graph|0
Collection|0
Key Value|0
Relational|0.33529
Memtable|0
Btree|0.00202
Hash|0.19543
Memory Cache|0.02048
Clustering|-0.09414
Separate R/W|0.30811
Sharding|-0.01427
CPU|1.29691
Memory|-0.25965

Database|Exp. Throughput|Rank Exp|Benchmark Score|Rank Benchmark
--------|----------|------------|-----|------
MariaDB ext|5042.86   |1           |140.42  |2
MariaDB  |4759.64   |2             |141.39  |1
Hypertable FS | 1770.85  |3        |127.18  |3
Hypertable no FS |1686.06   |4     |112.38  |4
MongoDB noShard | 1381.98  |5      |103.59  |6
MongoDB Shard |1348.44   |6        |101.15  |7
postgreSQL |1339.76   |7           |43.83  |11
postgreSQL ext |1208.61   |8       |42.86 |12
CouchDB|538.24 |9                  |85.16  |9
Cassandra Shard |465.48   |10      |100.55  |8
ElasticSearch|272.39|11            |107.98  |5
Cassandra noShard |262.36   |12    |74.76  |10
