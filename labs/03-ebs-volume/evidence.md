# Evidence

This section documents the practical steps completed during the EBS storage lab.

## EC2 Instance

EC2 instance successfully created for the lab.

![EC2 Instance Created](screenshots/01-instance-created.PNG)

## EBS Volume

A 5 GiB gp3 EBS volume was successfully created.

![EBS Volume Created](screenshots/02-ebs-volume-created.PNG)

## EBS Attachment

The EBS volume was successfully attached to the EC2 instance.

![EBS Volume Attached](screenshots/03-ebs-volume-attached.PNG)

## Disk Detection

The Linux operating system successfully detected the attached EBS volume.

![EBS Disk Detected](screenshots/04-ebs-disk-detected.PNG)

## Filesystem Configuration

The EBS volume was formatted using the XFS filesystem.

![EBS Formatted](screenshots/05-ebs-formatted.PNG)

## Volume Mount

The EBS volume was successfully mounted at `/mnt/ebs-storage`.

![EBS Mounted](screenshots/06-ebs-mounted.PNG)

## Data Write Test

Test data was successfully written to the EBS volume.

![EBS Data Test](screenshots/07-ebs-data-test.PNG)

## Final Verification

The EBS volume and stored data were successfully verified.

![Final Verification](screenshots/08-ebs-final-verification.PNG)
