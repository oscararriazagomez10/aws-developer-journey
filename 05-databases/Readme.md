# AWS Database Fundamentals

## Overview

This module covers the fundamentals of managed ddatabase services in AWS, with a focus on Amazon RDS, Amazon Aurora, and Amazon ElastiCahce.

These services provide managed solutions for relational databases and in-memory caching while reducing the operational overhead of infrastructure management.

## Topics Covered

### Amazon RDS

- Relattional database concepts
- Supported database engines
- DB instances
- DB Subnet Groups
- Security Groups
- Parameter Groups
- Multi-AZ deployments
- Read Replicas
- Cross-Region Read Replicas
- Automated backups
- Database snapshots
- Point-in-time recovery
- IAM Database Authentication
- SSL/TSL connections
- Disaster recovery


### Amazon Aurora

- Aurora architecture
- Aurora Cluster
- Writer and Reader instances
- Aurora Replicas
- Automatioc failover
- Aurora Serverless
- Aurora Global Database
- High availability
- Read scaling


### Amazon ElastiCache

- In-memory caching
- Redis / Valkey
- Memcached
- Primary and replica nodes
- Cluster Mode
- Read Replicas
- Cache strategies
- High availability



## Architecture Overview

AWS database services can be combined with application workloads to provide scalable and highly available architectures.

```text
                    AWS Application
                          |
             +------------+------------+
             |                         |
             v                         v
          Amazon RDS              ElastiCache
             |                    Redis/Valkey
             |
       +-----+-----+
       |           |
       v           v
     Writer      Replica
```

Aurora can provide additional read scaling and automated failover through Aurora Replicas.

# Key Concepts 

## High Availability

RDS Multi-AZ deployments provide high availability by maintaning a standby database in another availability Zone.

## Read Scaling

Read replicas allow read traffic to be distributed across additional database instances.

## Disaster Recovery

Cross-Region Read Replicas can be used to prepare for regional failures and provide a database that can be promoted in another aws Region

## Caching

ElastiCache can reduce database load and improve application response times by storing frequently accessed data in memory

# Security

Database security is based on multiple layers including:

- IAM
- Security Groups
- Encryption
- SSL/TLS
- Network isolation
- Authentication
- Least-privilege access

Detailed security recommendations are available in Security Best Practices.

Documentation
Database Notes
Security Best Practices

#  Practical Work

This module currently contains theoretical and conceptual learning.

No dedicated practical lab has been added because no hands-on database laboratory was completed as part of this module.

# Key Takeaways
Amazon RDS provides managed relational databases.
Multi-AZ improves database availability.
Read Replicas provide read scalability.
Cross-Region Read Replicas support disaster recovery.
Aurora provides a highly available cloud-optimized relational database architecture.
Aurora Replicas can improve read scalability and provide failover capabilities.
ElastiCache provides in-memory caching.
Redis/Valkey and Memcached are the main caching technologies covered.
Database security requires encryption, controlled network access, authentication, and least privilege.
