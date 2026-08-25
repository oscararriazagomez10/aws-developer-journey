# Amazon EC2

## Overview

Amazon Elastic Compute Cloud (EC2) provides resizable compute capacity in the AWS Cloud.

This module covers the fundamentals of launching, configuring, securing, and managing EC2 instances.

## Topics Covered

- EC2 fundamentals
- Amazon Machine Images (AMIs)
- Instance types
- Instance lifecycle
- Key pairs
- Security Groups
- User Data
- Instance metadata
- EBS storage
- Instance storage concepts
- Public and private IP addresses
- SSH and Systems Manager Session Manager
- High availability with Elastic Load Balancing
- Auto Scaling fundamentals

## EC2 Architecture

An EC2 instance is composed of several important components:

```text
                     Amazon EC2
                         |
        +----------------+----------------+
        |                |                |
       AMI         Instance Type     Security Group
        |                |                |
        +----------------+----------------+
                         |
                    EC2 Instance
                         |
              +----------+----------+
              |                     |
          Root Volume          Additional EBS
```
## Security

EC2 security depends on several AWS components:

Security Groups control network traffic.
IAM controls permissions and access to AWS resources.
Key pairs can be used for SSH authentication.
Systems Manager Session Manager provides secure instance access without requiring SSH.
Least-privilege permissions should be used for IAM roles.

For more information, see [Security Best Practices](security-best-practices.md).

Practical Labs

The practical EC2 exercises are maintained separately in the labs/ directory.

EC2 Labs
- [EC2 Instance Deployment](../labs/02-ec2-instance-deployment/)
- [ELB + Auto Scaling](../labs/03-instance-storage/)
- [Instance Storage](../labs/04-elb-asg/)
Detailed technical notes and commands are available in [Notes](notes.md).
