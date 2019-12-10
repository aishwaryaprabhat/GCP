# Storage

## Overview
### Use-Cases vs Technologies
Use Case | Non-cloud Technology | Cloud Technology
--- | --- | ---
Storage for compute, block storage | Persistent (hard disks), SSD | Persistent (hard disks), SSD
Storing media, immutable blob storage | File system like HDFS | Cloud Storage
SQL interface atop file data | Hive (SQL-like but MapReduce on HDFS) | BigQuery
Document database NoSQL | CouchDB, MongoDB (key-value/indexed DB) | DataStore optimize for fast reads
Fast scanning using row keys, NoSQL | HBase, Cassandra (columnar database) | BigTable (similar to HBase)
Transaction Processing (OLTP) | RDBMS like MySQL | CloudSQL (open-source)| Cloud Spanner (proprietary)
Analytics/Data Warehousr (OLAP) | Hive (SQL-like but MapReduce on HDFS) | BigQuery
Storage for compute, block storage along with mobile SDKs | | Cloud storage for Firebase
Fast random access with mobile SDKs | | Firebase realtime DB

## Block Storage 
- Unstructured data 
- Lowest level of storage - no abstraction at all
- Meant for use from VMs (or CPUs)
- Location tied to VM location
- Data stored in volumes called blocks
- Options available for block storage:
	- Persistent disks
		- Standard: traditional
		- SSD: faster and more expensive 
	- Local SSDs: attached to actual VM


## Cloud Storage
- Create buckets to store data
- Buckets are globally unique
	- Name (globally unique)
	- Location
	- Storage Class

### Storage Classes
- Multi-regional - frequent access from anywhere in the world
- Regional - frequent access from specific region
- Nearline - accessed once a month at max
- Coldline - accessed once a year at max


## BigQuery
- SQL interface atop file data
- Similar to Hive but far faster 
- Latency bit higher than BigTable, DataStore - prefer those for low latency
- No ACID properties - can't use for transaction processing
- Great for analytics/business intelligence/data warehouse (OLAP)
- Recall that OLTP needs strict write consistency
- SQL-like abstraction for non-relational data


## Cloud SQL, Cloud Spanner
- Relational databases - super structured, constraints etc
- ACID properties- use for transaction processing
- Not used for business intelligence or OLAP
- Offers horizontal scaling - bigger data, more instances, replication etc


## DataStore
- Document data eg XML or HTML - has a characteristic pattern
- Key-value structure
- Typically not OLAP or OLTP
- It is used for fast lookup on keys
- Query execution time depends on size of returned result and not size of dataset
- Fast reads and slow writes

## BigTable
- Columnar datastore, good for sparse data
- Fast scanning of sequential key values
- Data is sorted
- Sensitive to hot spotting 

## Review 
1) Databases are an abstraction on file storage. File storage is an abstraction on _________ storage

- Block storage