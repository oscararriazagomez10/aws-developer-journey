# Database Security Best Practices

## Overview

AWS database security should protect data, control access, minimize network exposure, and prevent unauthorized access.

Security should be applied across identity, networking, encryption, authentication, backups, and monitoring.

---

## 1. Use Least-Privilege IAM

Follow the principle of least privilege when granting access to database resources.

IAM policies should provide only the permissions required by the application or administrator.

Avoid using overly permissive policies such as:

```text
Action: *
Resource: *
```
when they are not required.

# 2. Keep Databases Private

Whenever possible, databases should not be directly accessible from the public Internet.

A common architecture is:
```
Internet
   |
   v
Application Load Balancer
   |
   v
Application
   |
   v
Private Database
```
RDS instances should normally be deployed in private subnets when public access is not required.

# 3. Use Security Groups

Security Groups should allow only the traffic required by the application.

For example:
```
Application Security Group
        |
        | TCP 5432
        v
PostgreSQL RDS
```
The database Security Group should allow connections from the application's Security Group rather than from the entire Internet.

Avoid rules such as:
```
0.0.0.0/0
```
for database ports unless there is a specific and justified requirement.

# 4. Encrypt Data at Rest

RDS and Aurora support encryption at rest.

Encryption protects stored database data, automated backups, snapshots, and other supported database storage.

AWS Key Management Service (AWS KMS) can be used to manage encryption keys.

Encryption should be enabled when handling sensitive or regulated data.

# 5. Encrypt Data in Transit

Database connections should use SSL/TLS whenever possible.

Encryption in transit protects data while it moves between:

- Applications
- RDS
- Aurora
- ElastiCache

For MySQL RDS, secure transport can be enforced using:
```
require_secure_transport = ON
```
# 6. Use IAM Database Authentication When Appropriate

IAM Database Authentication allows supported RDS databases to authenticate users through AWS IAM.

Supported RDS engines include:

- MySQL
- MariaDB
- PostgreSQL

This can reduce the need to distribute and manage long-lived database passwords.

IAM policies should still follow least-privilege principles.

# 7. Protect Database Credentials

Database credentials should never be hard-coded in:

- Source code
- Git repositories
- Application configuration committed to version control
- User Data scripts

AWS Secrets Manager can be used to securely store and manage database credentials.

Applications can retrieve secrets at runtime using appropriate IAM permissions.

8. Use Multi-AZ for High Availability

For production workloads that require high availability, consider using RDS Multi-AZ.

Multi-AZ provides a standby database in another Availability Zone and supports automatic failover.
```
Region
 |
 +----------------------+
 |                      |
 v                      v
Primary AZ           Standby AZ
RDS                    RDS
```
Multi-AZ should not be confused with Read Replicas.

Multi-AZ → High Availability

Read Replica → Read Scaling

# 9. Use Read Replicas Carefully

Read Replicas can improve read scalability and can also be used as part of a disaster recovery strategy.

However, replication is asynchronous in many RDS configurations, so applications should account for possible replication lag.

Read Replicas should not be considered a replacement for backups.

# 10. Plan for Disaster Recovery

A database should have a recovery strategy appropriate for its business requirements.

For regional failures, options can include:

- Cross-Region Read Replicas
- Aurora Global Database
- Database snapshots
- Automated backups

The strategy should consider:

- Recovery Time Objective (RTO)
- Recovery Point Objective (RPO)
- Replication lag
- Cost
- Operational complexity

# 11. Protect Backups and Snapshots

Backups and snapshots can contain sensitive database information.

Protect them by:

- Restricting IAM permissions.
- Encrypting supported backups.
- Controlling snapshot sharing.
- Applying appropriate retention policies.
- Avoiding unnecessary copies.

# 12. Secure ElastiCache

ElastiCache should also be protected from unauthorized access.

Recommended practices include:

- Deploying clusters inside a VPC.
- Using Security Groups.
- Restricting network access.
- Enabling encryption in transit when appropriate.
- Enabling encryption at rest when supported and required.
- Using authentication features where available.
- Applying least-privilege access.

# 13. Redis / Valkey Security

For Redis/Valkey workloads, consider:

- Network isolation.
- Authentication.
- Encryption in transit.
- Encryption at rest.
- Restricted Security Groups.
- Appropriate IAM permissions for AWS resources interacting with the cache.

Only trusted application components should be able to communicate with the cache.

# 14. Memcached Security

Memcached should be deployed in a controlled network environment.

Access should be restricted using Security Groups and network configuration.

Because Memcached is primarily a caching system, applications should not rely on it as the authoritative source of persistent data.

# 15. Monitor Database Activity

Database environments should be monitored for operational and security events.

Useful AWS services include:

- Amazon CloudWatch
- AWS CloudTrail
- AWS Config
- Amazon GuardDuty

Monitoring can help detect:

- Unauthorized access
- Configuration changes
- Unusual activity
- Performance problems
- Resource failures

# 16. Regularly Review Configuration

Database configurations should be reviewed regularly.

Check:

Public accessibility
Security Group rules
IAM permissions
Encryption
Backup configuration
Multi-AZ configuration
Parameter Groups
Monitoring
Network placement

Security should be continuously maintained rather than configured only during deployment.

# Security Checklist

Before deploying an RDS, Aurora, or ElastiCache workload, verify:

 - Database access follows least privilege.
 - Databases are private when possible.
 - Security Groups allow only required traffic.
 - Encryption at rest is enabled when appropriate.
 - SSL/TLS is used for connections.
 - Database credentials are securely managed.
 - IAM Database Authentication is used when appropriate.
 - Automated backups are configured.
 - Backup and snapshot access is restricted.
 - Multi-AZ is enabled for workloads requiring high availability.
 - Disaster recovery requirements are defined.
 - ElastiCache network access is restricted.
 - Database activity is monitored.
 - No credentials or secrets are stored in GitHub.

# Key Takeaways

The main principles for securing AWS databases are:

- Least privilege
- Private network access
- Restricted Security Groups
- Encryption at rest
- Encryption in transit
- Secure credential management
- Reliable backups
- High availability
- Disaster recovery
- Continuous monitoring
