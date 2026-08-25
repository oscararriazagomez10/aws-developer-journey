# Security Best Practices

## Load Balancer Security

- Use HTTPS for application traffic.
- Use TLS certificates with HTTPS listeners.
- Restrict inbound traffic with security groups.
- Use health checks to detect unhealthy targets.


## Auto Scaling Security

- Use IAM roles instead of hardcoded credentials.
- Use a secure AMI for EC2 instances.
- Keep instances update and patched.
- Use security groups with least-privilege rules.


## High Availanility

- Deploy EC2 instances across multiple Availability Zones.
- Use an Application Load Balancer to distributes traffic.
- Configure Auto Scaling to replace unhealthy instances.


## Monitoring 

- Monitor load balancer metrics with Amazon CloudWatch.
- Monitor EC2 health and application performances.
- Configure alarms for important metrics.


## Key principle

Security should be implemented at every layer of the architecture.

```text
Internet
   |
HTTPS
   |
Load Balancer
   |
Security Group
   |
EC2 Instances
   |
Auto Scaling
```
