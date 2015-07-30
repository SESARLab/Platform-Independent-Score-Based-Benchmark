# Benchmark Test #4

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

The tests and the training have been executed on **Environment 2**. 

#### Training Databases
Databases used in the training phase:
* CouchDB in 3 configurations
* ElasticSearch in 3 configurations
* MongoDB in 6 configurations
* PostgreSQL in 3 configurations
 
Specific configurations of the databases in the training set are defined in sheet "Training set" of [Test #4 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test4/ranking_Test4.xls).

#### Test Databases
Databases analyzed in the testing phase:
* CouchDB in 2 configurations
* ElasticSearch in 2 configurations
* MongoDB in 3 configurations
* PostgreSQL in 1 configurations

Specific configurations of the databases in the test set are defined in sheet "Test set" of [Test #4 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test4/ranking_Test4.xls).

#### Dependent Parameters
The following figures depict the functions generated during the training phase and used to calculate  platform-dependent parameters.

![Platform-dependent Parameters](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test4/parameters.jpg) 

#### Results
The following tables provide the weights and the computed ranking, calculated using the methodology implemented in the [Test #4 Ranking Excel file](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/raw/master/Test4/ranking_Test4.xls). The ranking is compared with the actual ranking based on the throughput values calculated during the experimental evaluation.

Parameter|Weight
--------|-------
Thrift|0
Map&Reduce|0
REST|0
Cursor|0
Collection|-0.02973
Companion SQL DB|0
Distributed B+ tree|0
Perfix Hash Table|0
OR-Junctions|-0.00717
AND-Junctions|0
Hot Deploy|0
Data Center Support|0.00651
Column Family|0.67046
Document|0.12102
Graph|0
Collection|0
Key Value|-0.04417
Relational|0
Memtable|0
Btree|-0.018
Hash|0
Memory Cache|0
Clustering|-0.06928
Separate R/W|0
Sharding|-0.01151
CPU|0.31282
Memory|0.57754

Database|Exp. Throughput|Rank Exp|Benchmark Score|Rank Benchmark
--------|----------|------------|-----|------


#### Discussion
We defined a training set with a limited variety in terms of configuration parameters, and evaluated the impact of
dependent parameters using abstract database configurations. Also, we deployed databases in different  physical environments, decreasing the precision of the experimental data given as input to our benchmark.

Our experiments show that the benchmark provides a very good level of quality. In particular, 6 out of the first 7 databases in rank_t are kept in the same position in rank_b (database #5 in rank_t is missing), with a single displacement between the first two databases (databases #1 and #2). 


However, also in this challenging scenario (worst case), we keep a good level of precision, which makes our approach suitable to narrow the search space of existing benchmarks. In fact, we can note that at least the first two databases in the real ranking are kept in the first two positions also in the ranking returned by our methodology. 
