# 🚀 Launch and Configure EC2 Instance

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**Platform:** AWS (us-east-1)
**Duration:** 30 minutes
**Tools:** AWS Console, Bash, EC2

## 📖 Overview
In this lab, I deployed a scalable virtual machine on AWS to host a static web application. This project demonstrates the fundamental capability of launching compute resources, configuring secure network access, and bootstrapping software installation.

**Key Achievements:**
-   Provisioned an **Amazon Linux 2023** EC2 instance (`t2.micro`).
-   Configured a **Security Group** acting as a firewall to allow SSH (22) and HTTP (80) traffic.
-   Deployed an **Apache Web Server** with a custom HTML page.

## 💼 Business Value
As a Sales Engineer, I understand that technical features must translate to business outcomes. This project demonstrates:
1.  **Speed to Market:** Ability to stand up infrastructure in minutes.
2.  **Cost Efficiency:** Utilizing rightsized compute instances (`t2.micro`) for development.
3.  **Security:** implementing least-privilege network access control.

---

## 🏗️ Architecture
![Architecture Diagram](img/architecture_diagram.png)
*(Placeholder: Simple architecture showing User -> Internet Gateway -> Security Group -> EC2 Instance)*

---

## 🛠️ Step-by-Step Implementation

### Prerequisites
*   An active AWS Account.
*   Basic understanding of TCP/IP networking (IPs, Ports).

### Phase 1: Network & Security
1.  **VPC:** Utilized the default VPC for rapid deployment.
2.  **Security Group:** Created `MyEC2Server_SG` to explicitly allow traffic only from necessary ports.
    *   *Port 22 (SSH):* Management access.
    *   *Port 80 (HTTP):* Public web access.

### Phase 2: Compute Provisioning
1.  Launched instance `MyEC2Server` using **Amazon Linux 2023 AMI**.
2.  Attached key pair `WhizKey` for secure SSH identity management.

### Phase 3: Configuration (User Data)
While this lab was performed manually, the configuration can be automated using the following script:

```bash
#!/bin/bash
sudo su
dnf update -y
dnf install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<html>Hi Whizlabs, I am a public page</html>" > /var/www/html/index.html
```

---

## ✅ Validation
**Endpoint:** `http://<Public-IP>/index.html`

**Result:**
The browser successfully displayed the hosted content, confirming that the web server is active and the security group is correctly configured.

![Lab Completion](img/lab_completion.png)

---

## 🔗 Next Steps
*   **Automation:** Convert this manual process into Terraform code (See my [Blog Post]()).
*   **Scalability:** Place this instance behind an Application Load Balancer.

---
*Lab completed as part of the Cloud Whizlabs training series.*
