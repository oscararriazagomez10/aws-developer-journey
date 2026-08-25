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


# Evidence

## 1. ALB Security Group

The ALB Security Group allows inbound HTTP traffic on port 80 from the Internet.

![ALB Security Group](evidence/01-alb-security-group.png)

## 2. EC2 Security Group

The EC2 Security Group allows HTTP traffict from the Application Load Balancer Security Group.

![EC2 Security Group](evidence/02-ec2-security-group.png)

## 3. Target Group

The target group contains the EC2 instances and performs HTTP health checks on port 80.

![Target Group](evidence/03-target-group.png)

## 4. Application Load Balancer 

The application Load balancer is configured with an HTTP listener on port 80 and forwards traffic to the target

![Application Load Balancer ](evidence/04-load-balancer-created.png)

## 5. Launch Template

The Launch Template defines the configuration used to launch EC2 instances, including the Amazon Linux 2023 AMI, IAM role, Security Group and User Data.

![Launch Template ](evidence/05-launch-template.png)

## 6. Auto Scaling Group

The Auto Scaling Group maintains the required EC2 capacity and manages the instances registered with the Target Group.

![Auto Scaling Group](evidence/06-.png)
## 7. Auto Scaling Replacement

After terminating an EC2 instance, the Auto Scaling Group automatically launched a replacement instance.

## 8. IAM and Systems Manager

The EC2 instances use an IAM role that allows management through AWS Systems Manager Session Manager.

## 9. ALB Application Test

The application was successfully accessed through the Application Load Balancer DNS name.



# The final environment provides a highly available web application where traffic is distributed across healthy EC2 instances and failed instances can be automatically replaced by the Auto Scaling Group.
