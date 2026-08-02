# Amazon EC2 Fundamentals Notes

## What is Amazon EC2?

Amazon EC2 (Elastic Compute Cloud) provides virtual servers in AWS.

It allows developers to:

- Deploy applications in the cloud.
- Configure computing resources.
- Manage servers without physical hardware.

---

## EC2 Main Components

### AMI (Amazon Machine Image)

A template used to create EC2 instances.

Includes:

- Operating system.
- Initial configuration.
- Software setup.

Example:

Amazon Linux 2023 AMI

---

### Instance Types

Define the resources of an EC2 instance.

Main categories:

| Type | Use Case |
|---|---|
| General Purpose | Balanced workloads |
| Compute Optimized | CPU intensive applications |
| Memory Optimized | Databases and large memory workloads |

---

### Key Pair

Used to securely connect to EC2 instances.

Example:

```bash
ssh -i key.pem ec2-user@public-ip
```

# Security Groups

Virtual firewall that controls EC2 traffic.

Example:

SSH  -> Port 22
HTTP -> Port 80
HTTPS -> Port 443

# EBS Storage

Persistent storage attached to EC2 instances.

Features:

- Data persistence.
- Snapshots.
- Storage management.

# EC2 Instance Lifecycle
Pending
   |
Running
   |
Stopped
   |
Terminated

- Running: Instance is active.
- Stopped: Instance is powered off but storage remains.
- Terminated: Instance is deleted.

# Important Concepts

| Concept        | Description                       |
| -------------- | --------------------------------- |
| AMI            | Template used to create instances |
| EC2 Instance   | Virtual server running in AWS     |
| Security Group | Controls network access           |
| EBS            | Persistent storage                |
| Key Pair       | Secure SSH authentication         |



