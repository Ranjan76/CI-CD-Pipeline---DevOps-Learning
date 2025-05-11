# CI/CD Pipeline – Real-World DevOps Workflow

## 🧠 Summary

This project documents a real-world CI/CD pipeline I have built and managed over the past 4 years as a DevOps professional. These handwritten notes represent a complete end-to-end automation pipeline, showcasing how I have used industry-standard tools in production to ensure code quality, security, and continuous delivery.

---

## ⚙️ Tools & Stages

### 1. 🧾 Planning & Coding
- **Jira/Ticket System** – For requirement tracking and task assignments.
- **Local Development** – Code is written and tested by developers before being committed.

### 2. 🚀 Pipeline Automation (CI/CD)

| Stage | Tool | Description |
|-------|------|-------------|
| **Code Push** | GitHub | Developers push code to a remote repository |
| **Trigger CI/CD** | Jenkins | Pipeline triggered on code push |
| **Build & Test** | Maven | Compiles code and runs unit tests |
| **Code Quality** | SonarQube | Analyzes code for bugs, code smells, and vulnerabilities |
| **Security Scan** | Aqua/Trivy | Scans Docker images for known vulnerabilities |
| **Artifact Build** | Maven | Packages and creates the build artifact |
| **Artifact Store** | Nexus Repository | Stores artifacts for later deployment |
| **Dockerize** | Docker | Creates Docker images and pushes to Docker Hub or private registry |
| **Deploy** | Kubernetes | Application is deployed to Kubernetes cluster |
| **Security Check** | kubeaudit | Scans the cluster for misconfigurations and security issues |

---

### 3. 📩 Notifications
- **Mail Notifications** – Pipeline sends success/failure updates to stakeholders.

---

### 4. 🔍 Monitoring

- **Website-Level Monitoring** (e.g., Blackbox Exporter):
  - Checks if the site is up
  - Monitors traffic and uptime

- **System-Level Monitoring**:
  - CPU, RAM usage
  - Infrastructure health

- **Visualization Tool**:
  - All monitoring data visualized in **Grafana**

---

## 📌 Outcome

The entire pipeline ensures that:
- Code meets quality and security standards
- Builds are automated, repeatable, and deployable
- Feedback is quick through notifications
- System and application health is always visible


📚 *This repository reflects real scenarios I've worked on — not just learning, but delivering production-ready DevOps solutions.*

🚀 DevOps Project Documentation
✅ Phase-Wise Breakdown (with MobaXterm)
🔹 Phase 1: Initial Setup – VPC, EC2, and Network
✅ Steps:
AWS Account

Select AWS region close to your location.

Make sure networking (VPC & internet access) is set up properly.

VPC Setup

Use default VPC (for simplicity) or create a new one.

Launch EC2 Instance

AMI: Ubuntu 22.04

Instance Type: t2.medium

Key Pair: Create or use existing .pem file

Security Group: Allow essential ports:

22 → SSH

80 → HTTP

443 → HTTPS

25, 465 → SMTP/Notifications

3000–10000, 50000–32767 → Application, Jenkins, Docker

6443 → Kubernetes API

Storage: Set e.g., 30 GB

Launch Instance

🔹 Phase 2: Connect Multiple EC2 VMs using MobaXterm
🎯 Objective: Create and SSH into multiple VMs using MobaXterm GUI
Instances to Launch:

Master Node

Slave 1

Slave 2

MobaXterm Setup

Open MobaXterm.

Go to "Session" → "SSH"

Remote Host: Public IP of EC2 instance

Username: ubuntu

Under "Advanced SSH settings":

Check “Use private key” → Browse and select your .pem file (converted to .ppk if needed using PuTTYgen)

Save session for each EC2 (master, slave1, slave2) for easy access.

Initial Configuration in Each VM

Update and install required packages

Set up hostname (optional):

bash
Copy
Edit
sudo hostnamectl set-hostname master
🔹 Phase 3: Master-Slave Connectivity
From Master EC2 (via MobaXterm terminal)

Copy SSH key to each slave:

bash
Copy
Edit
ssh-copy-id ubuntu@<slave1-private-ip>
ssh-copy-id ubuntu@<slave2-private-ip>
OR manually copy .pem to master and connect using ssh -i

Test Connection

From master: SSH into slaves and run commands like:

bash
Copy
Edit
ssh ubuntu@<slave1>
hostname
Goal: Master node should connect to slaves without password (passwordless SSH)

🔹 Phase 4: Git & CI/CD (Next Steps)
Git Setup

Create private Git repo

Push source code

Make repo visible to Jenkins

CI/CD

Setup Jenkins pipeline (master-slave)

Add:

Best practices

Mail notifications (port 465)

Security measures

🧰 Tools & Configurations Summary
MobaXterm: SSH GUI tool for connecting to EC2

Security Group: Firewall for ports

SSH: Secure connection from master to slaves

Hostname & Monitoring: Optional setup for better visibility

