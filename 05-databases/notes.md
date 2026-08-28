# AWS Database Notes

## 1. Amazon RDS

Amazon Relational Database Service (RDS) is a managed service that makes it easier to set up, operate, and scale relational databases in AWS.

RDS manages many administrative tasks such as:

- Database provisioning
- Backups
- Software patching
- Monitoring
- Automatic failure detection
- Recovery

### Supported Database Engines

Amazon RDS supports several relational database engines, including:

- PostgreSQL
- MySQL
- MariaDB
- Oracle
- Microsoft SQL Server
- IBM Db2

---

## 2. RDS DB Instances

A DB instance provides the compute and memory resources required to run a relational database.

Important configuration options include:

- Database engine
- Instance class
- Storage type
- Storage size
- Network configuration
- Security Groups
- Parameter Groups
- Backup configuration

---

## 3. RDS Storage

RDS can use different storage types depending on the database workload.

Common options include:

- General Purpose SSD
- Provisioned IOPS SSD

Storage selection should consider:

- Performance requirements
- Storage capacity
- IOPS requirements
- Workload characteristics
- Cost

---

## 4. Multi-AZ Deployments

Multi-AZ is designed primarily for high availability and automatic failover.

A typical architecture is:

```text
                RDS
                 |
        +--------+--------+
        |                 |
        v                 v
     Primary           Standby
     AZ-A               AZ-B
```
The standby instance is maintained in another Availability Zone.

If the primary database becomes unavailable, RDS can automatically fail over to the standby.
---
# Important

Multi-AZ is primarily a high availability and failover feature, not a read-scaling solution.

# 5. Read Replicas

Read Replicas are used to scale read-heavy workloads.

A primary database replicates data to one or more read replicas.

              Primary DB
                  |
        +---------+---------+
        |                   |
        v                   v
   Read Replica        Read Replica

Applications can send read requests to the replicas while writes continue to use the primary database.

## Cross-Region Read Replicas

A Read Replica can also be created in another AWS Region.

This can be useful for:

Disaster recovery
Geographic expansion
Reducing read latency for users in another region

Cross-Region replication is asynchronous.
---
# 6. RDS Backups

RDS provides automated backups that can be used for point-in-time recovery.

Automated backups include transaction logs and allow a database to be restored to a specific point within the configured backup retention period.

 ## DB Snapshots

DB snapshots are manually initiated backups of an RDS database.

Snapshots can be retained for long-term storage and can be used to create a new DB instance.
---
7. Parameter Groups

DB Parameter Groups are used to configure database engine parameters.

For example, MySQL can use:

require_secure_transport = ON

This forces connections to use secure transport.

Different database engines have different parameters and configuration options.
---
# 8. IAM Database Authentication

IAM Database Authentication allows applications to authenticate to supported RDS databases using AWS IAM instead of traditional database passwords.

Supported engines include:

MySQL
MariaDB
PostgreSQL

IAM Database Authentication can reduce the need to manage long-lived database passwords.
---
# 9. SSL/TLS Connections

RDS supports encrypted connections between applications and databases.

For MySQL, secure transport can be enforced using:

require_secure_transport = ON

For PostgreSQL, SSL connections can be enforced using the appropriate RDS parameter.

Encryption in transit protects database traffic from being transmitted in plaintext.
---
10. Amazon Aurora

Amazon Aurora is a relational database service compatible with MySQL and PostgreSQL.

Aurora is designed specifically for the AWS Cloud and provides high availability, scalability, and distributed storage.

## Aurora Cluster

An Aurora cluster normally consists of:

                 Aurora Cluster
                       |
             +---------+---------+
             |                   |
             v                   v
          Writer              Readers
             |                   |
             +---------+---------+
                       |
                Aurora Storage

The Writer instance handles write operations.

Reader instances can handle read operations.
---
11. Aurora Replicas

Aurora Replicas provide read scaling and improve availability.

Applications can send read traffic to Aurora Replicas while the Writer handles write operations.

If the Writer fails, Aurora can automatically promote an appropriate Replica to become the new Writer.
---
12. Aurora Endpoints

Aurora provides different endpoints for connecting applications to the cluster.

Cluster Endpoint

Used for connections to the current Writer.

Reader Endpoint

Used for read-only connections and can distribute connections across Aurora Replicas.

Custom Endpoints

Custom endpoints can be configured to connect applications to specific subsets of instances.
---
13. Aurora Storage

Aurora uses a distributed storage architecture.

The storage layer is shared across the instances in the cluster.

This allows Aurora to provide:

High durability
Automatic storage scaling
Replication
Fast recovery
---
14. Aurora Serverless

Aurora Serverless provides an on-demand database architecture where compute capacity can automatically adjust based on workload.

It is useful for workloads with variable or unpredictable traffic.

Aurora Serverless can reduce the need to manually provision database capacity.
---
15. Aurora Global Database

Aurora Global Database is designed for globally distributed applications and disaster recovery.

It allows an Aurora database to have secondary clusters in other AWS Regions.

Primary Region
      |
      | Global replication
      v
Secondary Region
      |
      v
Secondary Region

The primary cluster handles writes while secondary Regions can provide read access and disaster recovery capabilities.

16. Amazon ElastiCache

Amazon ElastiCache is a managed in-memory caching service.

It supports:

Valkey
Redis OSS
Memcached

Caching allows applications to retrieve frequently accessed data from memory instead of repeatedly querying the database.

Application
     |
     v
ElastiCache
     |
     | Cache miss
     v
   RDS

This can reduce database load and improve application performance.

17. Redis / Valkey

Redis and Valkey are in-memory data stores that support advanced features such as:

Replication
High availability
Automatic failover
Data structures
Persistence options

They can be used for:

Caching
Session storage
Real-time applications
Frequently accessed data
18. Redis Cluster Mode

Redis/Valkey can operate with Cluster Mode enabled or disabled.

Cluster Mode Disabled

There is a single primary shard with replicas.

             Primary
                |
        +-------+-------+
        |       |       |
      Replica Replica Replica

This architecture supports read scaling through replicas.

Cluster Mode Enabled

Data can be distributed across multiple shards.

       Cluster
     /    |    \
  Shard  Shard  Shard
    |      |      |
 Replicas Replicas Replicas

Cluster Mode Enabled provides horizontal scaling by distributing data across shards.

19. Memcached

Memcached is a simple, high-performance in-memory caching system.

It is designed primarily for caching and does not provide the same advanced capabilities as Redis/Valkey.

Memcached is useful when:

Simple caching is required.
Data can be distributed across multiple nodes.
Advanced persistence or replication features are not required.
20. RDS vs Aurora vs ElastiCache
Service	Main Purpose	Type
RDS	Managed relational database	Relational
Aurora	Cloud-optimized relational database	Relational
ElastiCache	In-memory caching	Cache
RDS

Choose RDS when you need a managed traditional relational database engine.

Aurora

Choose Aurora when you need a highly available and scalable relational database optimized for AWS.

ElastiCache

Choose ElastiCache when you need very fast access to frequently used data and want to reduce database load.

21. High Availability vs Read Scaling

A common exam distinction is:

Multi-AZ

Primarily provides:

High availability
Automatic failover
Standby infrastructure
Read Replicas

Primarily provide:

Read scaling
Additional read capacity
Cross-Region replication options
Multi-AZ
   ↓
High Availability

Read Replica
   ↓
Read Scaling
22. Disaster Recovery

For regional disaster recovery, a database can be replicated to another AWS Region.

For RDS:

Primary Region
      |
      v
Cross-Region Read Replica

If the primary Region becomes unavailable, the replica can be promoted to become an independent database capable of handling reads and writes.

For Aurora, Aurora Global Database can provide cross-Region replication and disaster recovery capabilities.

Key Takeaways
RDS is a managed relational database service.
Multi-AZ provides high availability and automatic failover.
Read Replicas provide read scaling.
Cross-Region Read Replicas can support disaster recovery.
RDS supports IAM Database Authentication for MySQL, MariaDB, and PostgreSQL.
SSL/TLS can encrypt database connections.
Aurora is a cloud-optimized relational database compatible with MySQL and PostgreSQL.
Aurora Replicas provide read scaling and failover capabilities.
Aurora Global Database supports cross-Region architectures.
ElastiCache provides in-memory caching.
Redis/Valkey supports advanced caching and replication features.
Memcached provides simple distributed caching.
Caching can reduce database load and improve application performance.
