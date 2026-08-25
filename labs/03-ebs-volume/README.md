# EC2 EBS Storage Lab

## Objective

Create, attach, configure, and use an Amazon EBS volume with an EC2 instance.

## Architecture

```text
EC2 Instance
     |
     | Attach
     v
  EBS Volume
    5 GiB
     |
     v
 XFS Filesystem
     |
     v
/mnt/ebs-storagE
```
## What I Practiced

- Created an EC2 instance.
- Created a 5 GiB gp3 EBS volume.
- Attached the EBS volume to the EC2 instance.
- Detected the volume from Linux.
- Formatted the volume with XFS.
- Mounted the volume.
- Created and verified a file on the EBS volume.


## Technologies

- Amazon EC2
- Amazon EBS
- Amazon Linux 2023
- AWS CLI /Linux Shell
- XFS


## Result

The EBS volume was successfully attached, formatted, mounted, and used to store data from the EC2 instance.
