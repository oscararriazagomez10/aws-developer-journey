# ELB + Auto Scaling Lab

## Overview

This lab demonstrates how to deploy a highly available web application using an Application Load Balancer (ALB) and an Auto Scaling Group (ASG).

The environment uses multiple Amazon EC2 instances running Apache HTTP Server. The Application Load Balancer distributes incoming HTTP traffic across healthy instances, while the Auto Scaling Group maintains the desired number of instances and automatically replaces unhealthy or terminated instances.

AWS Systems Manager Session Manager was also configured to provide secure instance access without requiring SSH.

## Architecture

```text
                         Internet
                            |
                            v
                Application Load Balancer
                       HTTP : 80
                            |
                            v
                     Target Group
                       /       \
                      /         \
                     v           v
                  EC2 #1       EC2 #2
                 Apache        Apache
                 Healthy       Healthy
                      \         /
                       \       /
                    Auto Scaling
                       Group
```
## AWS Services Used
- Amazon EC2
- Elastic Load Balancing (application Load Balancer)
- Target Groups
- Auto Scaling Groups
- Launch Templates
- AWS IAM
- AWS Sytems Manager Session Manager
- Security Groups

# Configuration

## Application Load Balancer

The Application Load Balancer listens for HTTP traffic on port 80 and forwards requests to the configured Target Group.


## Target Group

The Target Group uses HTTP health checks on port 80 to verify that the EC2 instances are available to receive traffic.


## Auto Scaling Group

The Auto Scaling Group maintains two EC2 instances and automatically launches a replacement instance when an instance is terminated.


## EC2 Instances

The instances use Amazon Linux 2023 with Apache HTTP Server installed through User Data.

## Systems Manager

AWS Systems Manager Session Manager was configured using an IAM role with the AmazonSSMManagedInstanceCore policy.

This allows secure access to the EC2 instances without opening SSH port 22.

## Result

The application was successfully accessed through the Application Load Balancer DNS name.

The Target Group reported healthy EC2 instances, and the Auto Scaling Group successfully replaced a terminated instance.

## Evidence

Detailed screenshots and explanations are available in evidence.md.