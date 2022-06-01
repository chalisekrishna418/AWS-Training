# Databases

## Relational Database Service (RDS)
- RDS is a AWS managed Database Service.
- You can use these database servers in AWS:
	- MariaDB on Amazon RDS
	- Microsoft SQL Server on Amazon RDS
	- MySQL on Amazon RDS
	- Oracle on Amazon RDS
	- PostgreSQL on Amazon RDS
- AWS RDS manages backups, software patching, automatic failure detection, and recovery for the Db Instances.
- Like EC2 Instances, there are also different db instance classes which defines the specs of those database instances.
- You can turn on automated backups, or manually create your own backup snapshots.
- For High Availability, You can enable multi AZ setup and use read replicas (upto 5 read replicas per db instance).
- You can enable encryption to encrypt the data that resides in RDS.
- Like EC2 instances, you can have reserved and ondemand RDS nut not spot RDS instances to efficiently use your cost of AWS.

**Aurora Instances**
- Aurora is part of the managed database service Amazon Relational Database Service (Amazon RDS) that is fully managed relational database engine compatible with MySQL and PostgreSQL.
- You can have one primary aurora instance and upto 15 Read replicas.
- Types of Aurora endpoints
	1. Cluster Endpoints
	2. Reader Endpoints
	3. Custom Endpoints
	4. Instance Endpoints

## DynamoDB
- Amazon DynamoDB is a fully managed NoSQL database service.
- You don't have to worry about hardware provisioning, setup and configuration, replication, software patching, or cluster scaling.
- You can scale up or scale down your tables' throughput capacity without downtime or performance degradation.
- Dynamodb Supports encryption at Rest
- You can create on-demand backups and enable point-in-time (PIT) recovery for your Amazon DynamoDB tables.With PIT, you can restore a table to any point in time during the last 35 days. 
- All data is automatically replicated across multiple Availability Zones in an AWS Region, providing built-in high availability and data durability.
- You can use global tables to keep DynamoDB tables in sync across AWS Regions.
- You can use AWS Database Migration Service (AWS DMS) to migrate data from a relational database or MongoDB to a DynamoDB table.

## ElastiCache
- Amazon ElastiCache is a fully managed, in-memory caching service supporting flexible, real-time use cases.
- Like EC2, Elasticache also has instance class that specifies the machine specs i.e. CPU, memory, CPU generation, etc.
- Amazon ElastiCache supports the Memcached and Redis cache engines.

### Elasticache Redis
- Existing applications that use Redis can use ElastiCache with almost no modification. 
- You can run your Redis by enabling or disabling the cluster mode.
- You can also create snapshots of your elasticache Redis Instances expect for `cache.t1.micro` nodes. There are some performance implications of backup operation.
- You can use Redis for :
	- as authenticating users with role-based access control.
	- as a database caching agent.
	- for primary database for storing simple key value pairs.
	- As a database to messages that would be consumed by message queues.

### Elasticache Memcached
- Usecases:
	- You need the simplest model possible.
	- You need to run large nodes with multiple cores or threads.
	- You need the ability to scale out and in, adding and removing nodes as demand on your system increases and decreases.
	- You need to cache objects.

## Lab
### Leveraging Elasticache redis and RDS as a cache and database host for application hosted in EC2 instance.

## Reading Materials
- [AWSDocs - What is AWS RDS?](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
- [AWSDocs - What is Amazon Dynamodb?](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
- [AWSDocs - Comparing Memcached and Redis](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/SelectEngine.html)