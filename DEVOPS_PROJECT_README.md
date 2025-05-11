
# 🚀 DevOps Project: AWS CI/CD with Docker, Jenkins, SonarQube, Nexus, and GitHub Integration

This repository documents the full journey of setting up a complete DevOps pipeline on AWS using EC2 instances, Docker, Jenkins, GitHub, SonarQube, and Nexus, along with monitoring and security practices.

---

## 📌 Phase 1: Infrastructure Setup

### ✅ EC2 & Network Setup
- Use AWS default VPC (or create new)
- Launch multiple EC2 instances (Ubuntu 22.04, t2.medium)
- Security group configuration:
  - `22` SSH
  - `80` HTTP
  - `443` HTTPS
  - `465`, `25` SMTP
  - `3000–10000` App Ports
  - `50000–32767` Jenkins, SonarQube
  - `6443` Kubernetes API

### ✅ Access via MobaXterm
- Use `.pem` or `.ppk` key
- Configure SSH for master and slave machines
- Setup passwordless SSH using `ssh-copy-id`

---

## 📌 Phase 2: GitHub Integration

- Create a **private GitHub repo**
- Clone via HTTPS using **Personal Access Token**:
  - GitHub > Settings > Developer Settings > Tokens
  - Generate token and give required permissions

```bash
git clone https://github.com/your-repo.git
git add .
git commit -m "add initial setup"
git push
```

---

## 📌 Phase 3: Jenkins Configuration

### Install Jenkins
```bash
sudo apt update
# Use scripted method (jen.sh)
chmod +x jen.sh
./jen.sh
```

### Jenkins Plugins
- ✅ Eclipse Temurin Installer
- ✅ Pipeline Maven Integration
- ✅ SonarQube Scanner
- ✅ Config File Provider

### Global Tool Configuration
- JDK 17 from Adoptium
- Maven 3.6.1
- Docker (install automatically)

---

## 📌 Phase 4: Docker & CI/CD Pipeline

### Docker Setup
```bash
sudo apt update
sudo apt install docker.io
```
- Verify with `docker ps`

### Docker Pipeline in Jenkins
- Configure Docker in Jenkins global tools
- Add credentials if needed

---

## 📌 Phase 5: SonarQube & Nexus

### SonarQube
- Search and run image:
```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube
```
- Default login: `admin / admin`

### Nexus
```bash
docker run -d --name nexus -p 8081:8081 sonatype/nexus3
```
- Retrieve admin password:
```bash
docker exec -it <container_id> /bin/bash
cat admin.password
```

---

## 📌 Phase 6: Kubernetes Prep (Next)
- Install Kube CLI
- Use Kube Client API
- Configure for Jenkins

---

## 📈 Goal
Build a complete, production-like CI/CD pipeline on AWS with monitoring, versioning, Docker image scanning, and artifact storage.

---

## ✅ Credits
Handwritten notes converted to README structure by Ranjan Kumar’s DevOps journey ✍️
