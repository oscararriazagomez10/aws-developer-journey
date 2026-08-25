# Commands

## 1. Connect to the EC2 Instance

Connect to the EC2 instance using SSH and the private key.

```bash
ssh -i web-lab-key.pem ec2-user @<PUBLIC-IP>

```

## 2.Detect the EBS Volume

List the block devices detected by the operating system.

```bash
lsblk

```
## 3. Format the EBS Volume

Create an XFS filesystem on the EBS volume.

```bash
sudo mkfs -t xfs /dev/nvme1n1

```

## 4. Create the Mount Point

Create a directory where the EBS volume will be mounted.

```bash
sudo mkdir /mnt/ebs-storage
```

## 5. Mount the EBS Volume

Mount the EBS volume to the new directory.

```bash
sudo mount /dev/nvme1n1 /mnt/ebs-storage
```

## 6. Verify the mount

Check the available storage and confirm that the EBS volume is mounted.

```bash
df -h /mnt/ebs-storage
```

## 7. Create Test Data

Create a test file and write data to the EBS volume.

```bash
sudo touch /mnt/ebs-storage/test.txt
```
```bash
echo "EBS storage lab completed successfully." | sudo tee /mnt/ebs-storage/test.txt
```
## 8. Verify the Data

Read the file to confirm that data was successfully written.

```bash
cat /mnt/ebs-storage/test.txt
```

## 9. Final Verification

Verify that the file exists and that the EBS volume is mounted.

```bash
ls -lah /mnt/ebs-storage
```

```bash
df -h /mnt/ebs-storage
```



