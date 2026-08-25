# ELB and Auto Scaling Lab

## Objective 

Build a higly available EC2 architecture using am Applicattion Load Balancer and an Auto Scaling Group.

## Architecture

```text
Internet
    |
    v
Application Load Balancer
    |
    v
Target Group
    |
    +----------+
    |          |
   EC2        EC2
    |          |
    +----------+
         |
        ASG
```

## What I Will Practice

- Create an application Load Balancer.
- Create a target Group.
- Configure EC2 instances as targets.
- Create an Auto Scaling Group.
- Configure health checks.
- Test traffict distribution.
- Verify instance rerplacement and Scaling.


## Expected Result

The Application Load Balancer should distribute traffic across healthy EC2 instances managed by the Auto Scaling Group.
