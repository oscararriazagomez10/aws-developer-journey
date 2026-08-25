# EC2 Security Best Practices

## Overview

Securing Amazon EC2 requires multiple layers of protection across identity, networking, operating systems, storage, and monitoring.

The goal is to follow the principle of least privilege while minimizing unnecessary network exposure.

## 1. Use Least-Privilege IAM Roles

EC2 instances should use IAM roles instead of storing AWS access keys on the instance.

Grant only the permissions required by the workload.

For example, an instance that only needs Systems Manager should receive the appropriate Systems Manager permissions rather than broad administrative access.

## 2. Restrict Security Group Rules

Security Groups should allow only the traffic required by the application.

Example:

```text
HTTP  → TCP 80
HTTPS → TCP 443
SSH   → TCP 22
```
Avoid:

SSH → 0.0.0.0/0

whenever possible.

SSH should normally be restricted to a trusted IP address or replaced with Systems Manager Session Manager.

## 3. Avoid Unnecessary Public Exposure

EC2 instances should not have public Internet access unless it is required.

A common architecture is:

Internet
   |
   v
Application Load Balancer
   |
   v
Private EC2 Instances

The Load Balancer handles public traffic while the EC2 instances remain protected from direct Internet access.

## 4. Use Systems Manager Session Manager

Session Manager can provide secure administrative access without requiring inbound SSH.

Advantages include:

No inbound port 22 required
No SSH key management
IAM-based access control
Centralized session management
Integration with AWS Systems Manager
## 5. Protect SSH Access

If SSH is required:

Use key-based authentication.
Restrict the source IP.
Avoid exposing port 22 to the entire Internet.
Protect private keys.
Never commit private keys to GitHub.

Example of a restricted rule:

Type: SSH
Protocol: TCP
Port: 22
Source: Trusted IP
## 6. Keep the Operating System Updated

Operating system packages should be regularly updated to address security vulnerabilities.

For Amazon Linux:

sudo dnf update -y

Updates should be tested appropriately before being deployed to production environments.

## 7. Use Secure AMIs

Use trusted and maintained AMIs.

Consider:

Official AWS AMIs
Regular security updates
Minimal installed software
Removal of unnecessary services
## 8. Protect EBS Volumes

EBS volumes should be encrypted whenever appropriate.

Encryption helps protect data at rest.

Important considerations include:

Enable EBS encryption.
Use appropriate AWS KMS keys when required.
Control access to snapshots.
Avoid sharing snapshots unnecessarily.
## 9. Protect Instance Metadata

EC2 Instance Metadata Service should be configured securely.

Where supported, prefer IMDSv2 to help reduce the risk of metadata credential exposure.

## 10. Avoid Hard-Coded Credentials

Never store AWS access keys, passwords, or other sensitive credentials directly in:

Source code
User Data
Git repositories
Configuration files

Use AWS IAM roles and appropriate secret-management services instead.

## 11. Monitor EC2 Instances

Use AWS monitoring and logging services to detect unusual activity.

Useful services include:

Amazon CloudWatch
AWS CloudTrail
AWS Systems Manager
Amazon GuardDuty

Monitoring helps identify operational and security issues.

## 12. Follow the Principle of Least Privilege

Every component should have only the permissions it requires.

This applies to:

IAM users
IAM roles
Security Groups
Applications
AWS services

Reducing unnecessary permissions limits the potential impact of a security incident.

Security Checklist

Before deploying an EC2 workload, verify:

 IAM roles use least privilege.
 Security Groups allow only required traffic.
 SSH is restricted or replaced with Session Manager.
 Unnecessary public access is disabled.
 EBS volumes are encrypted when appropriate.
 The operating system is updated.
 No credentials are hard-coded.
 Trusted AMIs are used.
 Monitoring is enabled.
 Sensitive information is not committed to GitHub.

##Key Takeaways

EC2 security should be implemented as a layered approach.

The most important principles are:

Least-privilege access.
Minimal network exposure.
Secure instance access.
Encryption of sensitive data.
Regular updates.
Continuous monitoring.
