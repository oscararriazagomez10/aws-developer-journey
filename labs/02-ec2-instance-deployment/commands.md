# EC2 Web Server Commands

## SSH Connection

```bash
ssh -i ec2-web-server-key.pem ec2-user@<EC2-PUBLIC-IP>
```

## System Update

```bash
sudo yum update -y
```
## Install Apache

```bash
sudo yum install httpd -y
```

## Start Apache

```bash
sudo systemctl start httpd
```

## Enable Apache on boot

```bash
sudo systemctl enable httpd
```
## Check Apache Status

```bash
sudo systemctl status httpd
```
