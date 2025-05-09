# 🖥️ AWS EC2 SSH Connection Project
![AWS](https://img.shields.io/badge/Built%20with-AWS-orange?style=flat&logo=amazonaws)![Project Status](https://img.shields.io/badge/status-in--progress-yellow)

This project demonstrates how to launch an Amazon EC2 instance and connect to it securely via SSH from your local terminal. It's a foundational AWS skill used in almost every cloud computing environment.

---

## Project Objective

To spin up an EC2 instance using Amazon Linux 2 and connect to it remotely via SSH using a `.pem` key pair, ensuring secure access.

---

## 🧰 Tools & Services Used

- **Amazon EC2**
- **Amazon Linux 2 AMI**
- **SSH (Secure Shell)**
- **AWS Key Pair (.pem file)**
- **Security Groups**
- **AWS Console or AWS CLI**

---

## ⚙️ Steps to Reproduce

### 1. 🚀 Launch an EC2 Instance

- Go to the [AWS EC2 Console](https://console.aws.amazon.com/ec2)
- Launch an instance with:
  - **AMI**: Amazon Linux 2 (64-bit)
  - **Instance type**: t2.micro (Free tier)
  - **Key Pair**: Create/download a `.pem` file
  - **Security Group**: Allow SSH (port 22) from your IP

| Setting               | Value                       |
| --------------------- | --------------------------- |
| **Name**              | `ec2-ssh-demo`              |
| **AMI**               | Amazon Linux 2 (64-bit x86) |
| **Instance type**     | `t2.micro` (Free Tier)      |
| **Key pair**          | Create new: `ec2-key.pem`   |
| **Network settings**  | Allow SSH (Port 22)         |
| **Storage**           | Default (8 GB gp2)          |
| **Advanced settings** | Leave default               |

#### Key Pair Creation
- Click Create new key pair
- Name: ``ec2-key``
- Type: RSA
- Format: ``.pem``
- Click Create key pair
Your browser will download ``ec2-key.pem`` — save it securely!
---

### 2. Set Permissions for the PEM File

- Your ``.pem ``file must have restricted permissions for SSH to work. Open your terminal and run:
  
   ``chmod 400 ec2-key.pem``

- This prevents the key from being publicly viewable.
  
### Step 3: Connect to Your EC2 Instance via SSH
 **Copy Your Public IP**
- From the [AWS EC2 Console](https://console.aws.amazon.com/ec2)
- From the EC2 Dashboard:
- Go to Instances
- Select your running instance
- Copy the **Public IPv4 address**

#### Run the SSH Command in CloudShell

  ``ssh -i ec2-key.pem ec2-user@<your-ec2-public-ip>``
  
- Replace ``<your-ec2-public-ip>`` with your real IP.
- Example:``ssh -i ec2-key.pem ec2-user@3.91.45.72``
