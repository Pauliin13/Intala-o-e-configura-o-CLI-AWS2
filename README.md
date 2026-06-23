# 🚀 AWS CLI Installation and Configuration Lab

![AWS](https://img.shields.io/badge/AWS-CLI-orange)
![EC2](https://img.shields.io/badge/Amazon-EC2-yellow)
![IAM](https://img.shields.io/badge/IAM-Security-blue)
![Linux](https://img.shields.io/badge/OS-Red%20Hat-red)
![Automation](https://img.shields.io/badge/Cloud-Automation-green)

## 📖 Project Overview

This project demonstrates the installation and configuration of AWS CLI v2 on a Red Hat Linux Amazon EC2 instance.

The lab covers remote access through SSH, AWS CLI installation, IAM credential configuration, and interaction with AWS services directly from the command line.

Command-line administration is one of the most important skills for Cloud Engineers, DevOps Engineers, and System Administrators, making AWS CLI a fundamental tool for infrastructure automation and management.

---

# 🎯 Objectives

* Install AWS CLI v2 on Linux
* Configure AWS credentials using IAM Access Keys
* Authenticate with AWS services
* Execute AWS CLI commands
* Access EC2 instances through SSH
* Work with IAM policies in JSON format
* Understand AWS automation concepts

---

# 🏗 Solution Architecture

```text
                 Local Computer
                        │
                        ▼
                    SSH Access
                        │
                        ▼
               Amazon EC2 Red Hat Linux
                        │
                        ▼
                    AWS CLI v2
                        │
                        ▼
                 AWS IAM Services
```

---

# ⚙️ AWS Services Used

| Service       | Purpose                        |
| ------------- | ------------------------------ |
| Amazon EC2    | Linux virtual machine          |
| AWS CLI       | Command-line administration    |
| IAM           | Identity and access management |
| SSH           | Secure remote access           |
| Red Hat Linux | Operating system               |
| JSON          | Structured output format       |

---

# 🛠 Implementation Steps

---

# Step 1 - Connect to EC2 via SSH

The first task consisted of accessing the EC2 instance remotely.

### Linux/macOS Command

```bash
ssh -i labsuser.pem ec2-user@PUBLIC_IP
```

### Components

| Parameter    | Description                     |
| ------------ | ------------------------------- |
| ssh          | Starts secure remote connection |
| -i           | Specifies the private key       |
| labsuser.pem | Authentication key              |
| ec2-user     | Default Linux user              |
| PUBLIC_IP    | EC2 public address              |

---

# Step 2 - Install AWS CLI v2

### Download Installer

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

Purpose:

Download the AWS CLI installation package from AWS.

---

### Extract Files

```bash
unzip -u awscliv2.zip
```

Purpose:

Extract installation files.

---

### Install AWS CLI

```bash
sudo ./aws/install
```

Purpose:

Install AWS CLI with administrative privileges.

---

### Verify Installation

```bash
aws --version
```

Example output:

```bash
aws-cli/2.x Python/3.x Linux/x86_64
```

---

# Step 3 - Explore IAM

IAM information was reviewed through the AWS Console.

Topics explored:

* IAM Users
* Policies
* Access Keys
* Secret Access Keys

### IAM Concepts

IAM is responsible for:

* Authentication
* Authorization
* Users
* Groups
* Policies
* Roles

---

# Step 4 - Configure AWS CLI

Command used:

```bash
aws configure
```

Configuration parameters:

| Setting               | Value          |
| --------------------- | -------------- |
| AWS Access Key ID     | Lab Access Key |
| AWS Secret Access Key | Lab Secret Key |
| Default Region        | us-west-2      |
| Output Format         | json           |

---

# Step 5 - Test AWS CLI Connectivity

Command executed:

```bash
aws iam list-users
```

### Result

The command returned IAM users in JSON format, confirming:

* Successful installation
* Valid authentication
* Connectivity with AWS services

---

# Challenge - Export IAM Policy

### List Local Policies

```bash
aws iam list-policies --scope Local
```

---

### Retrieve Policy Version

```bash
aws iam get-policy-version \
--policy-arn POLICY_ARN \
--version-id v1 > lab_policy.json
```

Purpose:

Export IAM policy content into a JSON file.

---

# 💻 Commands Used

## SSH Access

```bash
ssh -i labsuser.pem ec2-user@PUBLIC_IP
```

## Download AWS CLI

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

## Install AWS CLI

```bash
sudo ./aws/install
```

## Configure AWS CLI

```bash
aws configure
```

## List IAM Users

```bash
aws iam list-users
```

## List Policies

```bash
aws iam list-policies --scope Local
```

---

# 📚 Concepts Demonstrated

| Concept    | Description                         |
| ---------- | ----------------------------------- |
| AWS CLI    | AWS administration through terminal |
| SSH        | Secure remote access                |
| IAM        | Identity and access management      |
| Access Key | Authentication credential           |
| Secret Key | Private credential                  |
| ARN        | AWS resource identifier             |
| JSON       | Data format                         |
| sudo       | Administrative privilege            |

---

# 🎓 Learning Outcomes

This project provided hands-on experience with:

* AWS CLI installation and configuration
* Linux administration
* SSH connectivity
* IAM authentication
* AWS command-line operations
* Infrastructure automation concepts
* Policy management
* JSON data manipulation

---

# 📊 Skills Demonstrated

* AWS CLI
* Amazon EC2
* IAM
* Linux Administration
* SSH
* Security Concepts
* JSON
* Infrastructure Automation
* Cloud Operations
* Command-Line Management

---

# 📂 Repository Structure

```text
aws-cli-installation-lab
│
├── README.md
├── images
│     ├── architecture.png
│     ├── ssh-connection.png
│     ├── aws-configure.png
│     ├── iam-users.png
│     └── cli-output.png
│
├── scripts
│     ├── install-aws-cli.sh
│     ├── configure-cli.sh
│     └── export-policy.sh
│
└── docs
      └── lab-notes.md
```

---

# 📌 Author

**Paulo Henrique

AWS Cloud Practitioner Candidate | Cloud Computing Enthusiast

---

## ⭐ If you found this project useful, feel free to star the repository.
