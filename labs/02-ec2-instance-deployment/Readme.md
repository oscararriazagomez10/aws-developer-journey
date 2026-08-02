# EC2 Web Server Deployment Lab

##  Lab Overview

This lab demonstrates how to deploy a basic web server using an Amazon EC2 instance.

The objective is to create a Linux EC2 instance, configure secure access, install a web server, and verify that the application is accessible.

---

##  Lab Objectives

By completing this lab, I learned how to:

- Launch an EC2 instance.
- Configure Security Groups.
- Connect to an instance using SSH.
- Install and configure a web server.
- Validate application availability.

---

##  Architecture
User

|

Internet

|

Security Group

|

EC2 Instance

|

Apache Web Server


---

## 🛠️ AWS Services Used

| Service | Purpose |
|---|---|
| Amazon EC2 | Virtual server hosting the application |
| Security Groups | Control network access |
| EBS | Persistent storage |
| SSH | Secure server connection |

---

## ⚙️ EC2 Configuration

Instance configuration:

| Setting | Value |
|---|---|
| Operating System | Amazon Linux 2023 |
| Instance Type | t2.micro |
| Storage | 8 GB gp3 EBS |
| Access Method | SSH Key Pair |

---

## 🔐 Network Configuration

Security Group rules:

| Type | Port | Purpose |
|---|---|---|
| SSH | 22 | Remote administration |
| HTTP | 80 | Web access |

---

## 🚀 Deployment Steps

The deployment process:

1. Create an EC2 instance.
2. Configure Security Group rules.
3. Connect through SSH.
4. Install Apache web server.
5. Deploy a test webpage.
6. Verify the application works.

---

## ✅ Validation

The web server is validated by accessing:

http://<EC2-PUBLIC-IP>


Expected result:

EC2 Web Server Successfully Deployed


---

## 📚 Key Learnings

After completing this lab, I understand:

- How to deploy an EC2 instance.
- How to configure secure network access.
- How to manage a Linux server in AWS.
- How applications can run on EC2 infrastructure.
