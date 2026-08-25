# EC2 Notes

## 1. What is Amazon EC2?

Amazon Elastic Compute Cloud (EC2) provides scalable virtual servers in the AWS Cloud.

An EC2 instance is a virtual machine that can be configured with different compute, memory, storage, and networking resources depending on the workload.

## 2. Amazon Machine Images (AMIs)

An Amazon Machine Image (AMI) is a template used to launch an EC2 instance.

An AMI can contain:

- Operating system
- Application software
- Configuration settings
- Required packages

Common examples include Amazon Linux, Ubuntu, and Windows Server.

## 3. Instance Types

EC2 offers different instance types optimized for specific workloads.

The main categories include:

- General purpose
- Compute optimized
- Memory optimized
- Storage optimized
- Accelerated computing

The instance type determines the available CPU, memory, networking performance, and other resources.

## 4. Instance Lifecycle

An EC2 instance can move through several states:

```text
Pending
   |
   v
Running
   |
   +----------+
   |          |
   v          v
Stopped    Terminated
```

Running

The instance is active and can process workloads.

Stopped

The instance is shut down but can usually be started again later.

Terminated

The instance is permanently deleted and cannot normally be restarted.

## 5. Key Pairs

Key pairs are used to securely authenticate to EC2 instances.

For Linux instances, SSH can use the private key associated with the key pair.

The private key must be protected and should never be committed to a Git repository.

## 6. Security Groups

Security Groups act as virtual firewalls for EC2 instances.

They control inbound and outbound network traffic.

Examples:

HTTP  → TCP 80
HTTPS → TCP 443
SSH   → TCP 22

Security Groups are stateful, meaning that return traffic for an allowed connection is automatically allowed.

## 7. User Data

EC2 User Data allows commands or scripts to run during the initial instance launch.

Example:
#!/bin/bash

dnf update -y
dnf install -y httpd

systemctl enable httpd
systemctl start httpd

echo "<h1>Hello from EC2</h1>" > /var/www/html/index.html

User Data is useful for automating initial instance configuration.

## 8. Instance Metadata

EC2 Instance Metadata provides information about a running instance.

It can provide information such as:

Instance ID
Private IP address
Availability Zone
IAM role information

The Instance Metadata Service is available from within the EC2 instance.

## 9. Storage

EC2 instances can use different types of storage.

Amazon EBS

Elastic Block Store (EBS) provides persistent block storage for EC2 instances.

EBS volumes can be:

Created independently
Attached to EC2 instances
Detached
Reattached
Resized
Instance Store

Instance Store provides temporary block-level storage physically associated with the host.

Instance Store data is ephemeral and can be lost when the instance is stopped, terminated, or the underlying host is replaced.

## 10. Networking

EC2 instances can have:

Private IPv4 addresses
Public IPv4 addresses
Elastic IP addresses

A private IP address is used for communication inside the VPC.

A public IP address allows communication with the Internet when the network configuration permits it.

## 11. SSH

SSH provides secure remote access to Linux EC2 instances.

The default SSH port is:

TCP 22

However, SSH access should be restricted to trusted sources whenever it is required.

AWS Systems Manager Session Manager can also provide secure instance access without opening inbound SSH.

## 12. IAM Roles

IAM roles allow EC2 instances to access AWS services securely without storing long-term AWS credentials on the instance.

For example, an EC2 instance can use an IAM role to communicate with Systems Manager.

## 13. Systems Manager Session Manager

Session Manager provides interactive shell access to managed EC2 instances without requiring:

SSH
An inbound port 22 rule
Management of SSH keys

The EC2 instance requires the appropriate IAM permissions and Systems Manager connectivity.

## 14. High Availability

EC2 instances can be combined with other AWS services to improve availability.

For example:

Internet
   |
   v
Application Load Balancer
   |
   v
Target Group
   |
   +------------+
   |            |
   v            v
 EC2          EC2
   |            |
   +-----+------+
         |
   Auto Scaling
      Group

An Application Load Balancer distributes traffic between healthy instances.

An Auto Scaling Group can automatically launch replacement instances when required.

## Key Takeaways
- EC2 provides scalable virtual compute capacity.
- AMIs are templates used to launch instances.
- Instance types determine available compute resources.
- Security Groups control network traffic.
- User Data automates initial configuration.
- EBS provides persistent block storage.
- Instance Store provides temporary storage.
- IAM roles provide secure AWS access to EC2.
- Session Manager can provide secure access without SSH.
- Auto Scaling and Load Balancing can improve application availability.
