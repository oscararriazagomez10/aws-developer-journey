# Elastic Load Balancing  and Auto Scaling

## Elastic Load Balancing (ELB)

Elastic Load Balancing distributes incoming traffic across multiple targets.

Key points:

- Distributes application traffic.
- Improves availability.
- Supports health checks.
- Removes unhealthy tragets from traffic.
- Works with Auto Scaling.

## Auto Scaling Groups (ASG)

An auto Scaling Group manages a fleet OF EC2 instances.

Key points:

- Maintains the desired number of instances.
- Automatically launches new instances when requiered.
- Terminates instances when capacity is no longer needed.
- Replaces unhealthy instances.
- Can scale based on demand.


## ELB + ASG

ELB and ASG can work together  to build highly available applications.

```text
Users
  |
  v
Load Balancer
  |
  +--------+
  |        |
 EC2      EC2
  |        |
  +--------+
      |
     ASG
```

## Key Takeaways

- ELB distributes traffic.
- ASG manages EC2 capacity.
- Health checks help maintain availability.
- Scaling policies allow applications to responds to demand.
- ELB + ASG improves scalibility and faul tolerance.


