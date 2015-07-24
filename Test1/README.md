# Benchmark Test #1

## Experimental Setting

#### Workload
The workload used in the experiment is **95% Read** and **5% Write**. Databases are populated with 100k records and are tested with 10k queries according to the read/write profile, using 50 threads simulating parallel requests.

#### Training Databases
Databases used in the training phase:
* MongoDB
* MariaDB
* Hypertable

#### Test Databases
Databases expoloited in the testing phase:
* MongoDB
* MariaDB
* Hypertable
* PostgreSQL
* Cassandra

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

Database|Experimental Evaluation|Benchmark Evaluation
        |Throughput|Rank_t      |Score|Rank_b
--------|----------|------------|-----|------


the normalized Kendall's tau distance between \rank{t} and \rank{b} is 0.36, while the normalized Spearman's footrule is 0.26. Also, the results show a better quality for \rank{b} when we penalize more total displacement and pairwise disagreements involving elements near the head of \rank{t}. By assigning linear weights `s_1=10`, `s_2=9`, `s_3=8`, `s_4=7`, `s_5=6`, `s_6=5`, `s_7=4`, `s_8=3`, `s_9=2`, `s_10=1`, the normalized Kendall's tau becomes `0.26`, with an increase in quality of `27.8%`, while the normalized Spearman's footrule becomes `0.16`, with an increase in quality of `38.5%`. Moreover, 4 out of the first 5 databases in \rank{t} are kept in the same position in \rank{b}, corresponding to a precision of `80%`. We observe that although \db{5}, the only database not maintained in the top-5 ranking, is moved from the 4th position to 8th position, its score (`36.40`) is very similar to the ones of databases in the 6th (`38.91`) and 7th (`36.82`) positions. The latter result shows that different databases with similar configurations can be ranked with similar scores, which make the decision about which database to select hard and often random. This is particularly relevant when similar scores are provided for top-ranked databases. In this case, the adoption of our benchmark in conjunction with existing benchmarks could represent a proper balance between overhead and quality.
