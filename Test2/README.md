# Benchmark Test #2

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

The tests and the training have been executed on Environment 1 and Environment 2. For each database the target environment has been specified.

#### Training Databases
Databases used in the training phase:
* MongoDB (Env. 1) in 6 configurations
* MariaDB (Env. 1) in 6 configurations
* Hypertable (Env. 1) in 6 configurations
* CouchDB (Env. 2) in 3 configurations
* ElasticSearch (Env. 2) in 3 configurations

Specific configurations of the databases in the training set are defined in sheet "Training set" of [Test #2 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test2/ranking_Test2.xls).

#### Test Databases
Databases analyzed in the testing phase:
* MongoDB (Env. 1) in 2 configurations
* MariaDB (Env. 1) in 2 configurations
* Hypertable (Env. 1) in 2 configurations
* Cassandra (Env. 1) in 2 configurations
* PostgreSQL (Env. 1) in 2 configurations
* CouchDB (Env. 2) in 1 configurations
* ElasticSearch (Env. 2) in 1 configurations

Specific configurations of the databases in the test set are defined in sheet "Test set" of [Test #2 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test2/ranking_Test2.xls).

#### Dependent Parameters
The following figures depict the functions generated during the training phase and used to calculate  platform-dependent parameters.

![Platform-dependent Parameters](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test1/parameters.jpg) 

#### Results
The following tables provide the weights and the computed ranking, calculated using the methodology implemented in the [Test #2 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test2/ranking_Test2.xls). The ranking is compared with the actual ranking based on the throughput values calculated during the experimental evaluation.

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

Database|Exp. Throughput|Rank_t|Benchmark Score|Rank_b
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

#### Discussion
We defined a training set with a limited variety in terms of configuration parameters, and evaluated the impact of dependent parameters using abstract database configurations. Also, we deployed databases in different physical environments, decreasing the precision of the experimental data given as input to our benchmark.

Apparently, our experiments show an insufficient level of quality for our benchmark. However, we observe that the first two databases in the real ranking are kept in the first two positions also in the ranking returned by our methodology. Therefore, also in a challenging scenario that considers different physical environments, our approach can be used to narrow the search space of existing benchmarks, substantially reducing their complexity.
