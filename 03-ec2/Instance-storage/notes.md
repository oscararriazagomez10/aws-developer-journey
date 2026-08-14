# EC2 Instance Storage

## Overview

EC2 instances can use different types of storage depending on the workload and data requirements.

## EBS Volumes

Amazon EBS provides persistent block storage for EC2 instances.

Key characteristics:

- Persistent storage
- Independent from the EC2 instance lifecycle
- Can be attached to EC2 instances
- Supports different volume types
- Suitable for operating systems and application data

## Instance Store

Instance Store provides temporary block storage physically attached to the host.

Key characteristics:

- High performance
- Temporary storage
- Data is lost when the instance is stopped, terminated, or the underlying host fails
- Suitable for temporary data and caching

## EBS vs Instance Store

| Feature | EBS | Instance Store |
|---|---|---|
| Persistence | Persistent | Temporary |
| Storage location | Network-attached | Physically attached |
| Data survives stop | Yes | No |
| Typical use | OS and application data | Cache and temporary data |

## Key Takeaways

- EBS is persistent block storage for EC2.
- Instance Store is temporary storage.
- Storage type should be selected based on application requirements.
- EBS volume type affects performance and cost.
