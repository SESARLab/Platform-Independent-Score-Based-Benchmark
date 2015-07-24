# Benchmark Test #1

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

#### Training Databases
Databases used in the training phase:
* MongoDB in 6 configurations
* MariaDB in 6 configurations
* Hypertable in 6 configurations

Specific configurations of the databases in the training set are defined in sheet "Training set" of [Test #1 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test1/ranking_Test1.xls).

#### Test Databases
Databases expoloited in the testing phase:
* MongoDB in 2 configurations
* MariaDB in 2 configurations
* Hypertable in 2 configurations
* PostgreSQL in 2 configurations
* Cassandra in 2 configurations

Specific configurations of the databases in the test set are defined in sheet "Test set" of [Test #1 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test1/ranking_Test1.xls).

#### Dependent Parameters
The following figures depicts the functions calculating the platform-dependent parameters as calculated during the training phase.

![Platform-dependent Parameters](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test1/parameters.jpg) 

#### Results
The following tables provide the weights and the computed ranking, calculated using the methodology implemented in the [Test #1 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test1/ranking_Test1.xls). The ranking is compared with the actual ranking based on the throughput values calculated during the experimental evaluation.

Parameter|Weight
--------|-------
Thrift|0
Map&Reduce|0
REST|0
Cursor|-0.00049
Collection|0.08026
Companion SQL DB|0
Distributed B+ tree|0
Perfix Hash Table|0
OR-Junctions|0
AND-Junctions|0
Hot Deploy|0
Data Center Support|0.01046
Column Family|0
Document|0
Graph|0.16202
Collection|0
Key Value|0
Relational|0
Memtable|0
Btree|0
Hash|0
Memory Cache|0.00042
Clustering|0.0233
Separate R/W|1
Sharding|-0.03855
CPU|1.39046
Memory|-0.32993

Database|Exp. Throughput|Rank Exp|Benchmark Score|Rank Benchmark
--------|----------|------------|-----|------
MariaDB |5042.86   |1           |85.72 |1
MariaDB ext |4759.64   |2           |85.68 |2
Hypertable FS | 1770.85  |3           |48.35 |3
Hypertable no FS |1686.06   |4           |36.40 |8
MongoDB noShard | 1381.98  |5           |40.74 |5
MongoDB Shard |1348.44   |6           |36.82 |7
postgreSQL |1339.76   |7           |18.67 |10
postgreSQL ext |1208.61   |8           |18.70 |9
Cassandra Shard |465.48   |9            |38.91 |6
Cassandra noShard |262.36   |10           |47.99 |4

#### Discussion
We defined a training set with a limited variety in terms of configuration parameters, and evaluated the impact of
dependent parameters using abstract database configurations. In particular, 4 out of the first 5 databases in rank_t are kept in the same position in rank_b, corresponding to a precision of `80%`. We observe that although *Hypertable no FS*, the only database not maintained in the top-5 ranking, is moved from the 4th position to 8th position, its score (`36.40`) is very similar to the ones of databases in the 6th (`38.91`) and 7th (`36.82`) positions. The latter result shows that different databases with similar configurations can be ranked with similar scores, which make the decision about which database to select hard and often random. This is particularly relevant when similar scores are provided for top-ranked databases. In this case, the adoption of our benchmark in conjunction with existing benchmarks could represent a proper balance between overhead and quality.

Our experiments show that the benchmark provides a good level of quality also when the training set and the experimental evaluation of dependent parameters are designed to introduce a not-negligible level of imprecision. 
