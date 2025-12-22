# 🚀 Launch and Configure EC2 Instance

**Platform:** AWS  
**Duration:** 30 minutes  
**Region:** US East (N. Virginia) `us-east-1`

## 📖 Overview
In this lab, I gained practical experience launching Amazon EC2 instances using Amazon Machine Images (AMI) and managing access via key pairs. I successfully deployed a virtual machine, installed an Apache web server, and hosted a custom HTML page.

### 🎯 Objectives
- **Launch an EC2 Instance:** Configure and provision a virtual machine in the cloud.
- **SSH Access:** Connect to the instance securely using a key pair.
- **Web Server Deployment:** Install and configure Apache (httpd).
- **Host Content:** Create and publish a static web page visible via public IP.

---

## 🏗️ Architecture
![Architecture Diagram](img/architecture_diagram.png)
*(Please place your architecture screenshot here named `architecture_diagram.png`)*

---

## 🛠️ Step-by-Step Implementation

### Task 1: Sign in to AWS Console
1.  Logged into the AWS Management Console.
2.  Ensured the region was set to **US East (N. Virginia) us-east-1**.

### Task 2: Provision Default VPC
*(If required)*
1.  Checked for a valid default VPC.
2.  Created a new default VPC to ensure network connectivity.

### Task 3: Launch EC2 Instance
1.  **Navigate to EC2:** Accessed the EC2 Dashboard.
2.  **Launch Instance:**
    -   **Name:** `MyEC2Server`
    -   **AMI:** Amazon Linux 2023 AMI
    -   **Instance Type:** `t2.micro` (Free tier eligible, 1 vCPU, 1 GiB Memory)
3.  **Key Pair:**
    -   Created a new key pair named `WhizKey` (.pem format) for SSH access.
4.  **Network Settings & Security Group:**
    -   **Auto-assign Public IP:** Enabled
    -   **Security Group Name:** `MyEC2Server_SG`
    -   **Inbound Rules:**
        -   **SSH (Port 22):** Allowed from Anywhere (for management)
        -   **HTTP (Port 80):** Allowed from Anywhere (for web access)

> **Concept:** A security group acts as a virtual firewall to control inbound and outbound traffic.

![EC2 Launch Config](img/ec2_launch.png)

### Task 4: Connect to Instance (SSH)
1.  Selected the running instance `MyEC2Server`.
2.  Used **EC2 Instance Connect** to open a terminal directly in the browser.

### Task 5: Install Apache Web Server
Ran the following commands to update the system and install the server:

```bash
# Switch to root user
sudo su

# Update package repository
dnf update -y

# Install Apache (httpd)
dnf install httpd -y

# Start the service
systemctl start httpd

# Enable service to start on boot
systemctl enable httpd

# Verify status
systemctl status httpd
```

### Task 6: Publish Web Page
Created a custom index.html file to serve content.

```bash
echo "<html>Hi Whizlabs, I am a public page</html>" > /var/www/html/index.html
```

Restarted the web server to ensure changes took effect:
```bash
systemctl restart httpd
```

---

## ✅ Validation & Results
To verify the deployment, I accessed the public IPv4 address of the instance in a browser:
`http://<Public-IP>/index.html`

**Result:**
The browser successfully displayed: **"Hi Whizlabs, I am a public page"**

![Lab Completion](assets/lab_completion.png)
*(Please place your final validation screenshot here named `lab_completion.png`)*

---
*Lab completed on Whizlabs.*
