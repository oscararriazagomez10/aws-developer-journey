# EC2 Security Best Practices

## 🔐 Overview

Security is a critical part of managing EC2 instances in production environments.

The main goals are:

- Protect access to servers.
- Reduce attack surface.
- Follow the principle of least privilege.
- Monitor and maintain infrastructure.

---

# Identity and Access Management (IAM)

## Use IAM Roles Instead of Access Keys

EC2 instances should use IAM Roles to access AWS services.

Avoid storing AWS credentials inside the server.

Bad practice:

Access Key
+
Secret Key
stored on EC2


Recommended:
EC2 Instance

  |

IAM Role

  |

AWS Services


Benefits:

- More secure authentication.
- Automatic credential rotation.
- Better permission management.

---

# Secure SSH Access

SSH is commonly used to access Linux EC2 instances.

Best practices:

- Use SSH key pairs.
- Do not use passwords.
- Restrict SSH access to trusted IP addresses.
- Never expose SSH to everyone.

Example:
Allowed:

My IP → Port 22

Avoid:

0.0.0.0/0 → Port 22

---

# Security Groups

Security Groups act as virtual firewalls for EC2 instances.

Best practices:

- Allow only required ports.
- Remove unused rules.
- Follow the principle of least privilege.

Example:

HTTP → Port 80
HTTPS → Port 443
SSH → Port 22

Only open services that are necessary.

--- 

# Operating System Updates

Keeping the operating system updated reduces security risks.

Example:

```bash
sudo yum update -y
```
Recommended:

- Apply security patches regularly.
- Remove unnecessary software.
- Monitor vulnerabilities.

# Data Protection
EC2 storage should be protected.

Best practices:

- Use encrypted EBS volumes.
- Create regular snapshots.
- Control access to stored data.

Example:
EC2 Instance

      |

Encrypted EBS Volume

# Monitoring and Logging
Production EC2 environments should be monitored.

Recommended services:

- Amazon CloudWatch.
- AWS CloudTrail.

Monitor:

- CPU usage.
- Network activity.
- Instance status.
- Security events.

# Cost and Security Optimization.
Good security practices also improve cost management.

Examples:

- Remove unused instances.
- Delete unused volumes.
- Use appropriate instance sizes.
- Monitor resource consumption.
