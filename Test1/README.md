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

![Platform-dependent Parameters](https://github.com/SESARLab/Platform-Independent-Score-Based-Benchmark/Test1/parameters.jpg) 
#### Results
