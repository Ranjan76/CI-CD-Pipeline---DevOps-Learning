# CI-CD-Pipeline---DevOps-Learning
CI/CD Pipeline - DevOps Learning

## 🧠 Summary

This project is a reflection of my hands-on experience in building and managing CI/CD pipelines over the past 4 years. The handwritten notes represent a real-world workflow I have followed in production environments while working with tools like Jenkins, Maven, SonarQube, Nexus, and Docker.

I have documented this process to showcase my practical understanding of DevOps workflows — from code integration to automated testing, artifact management, and deployment.

## 📷 Notes

![CI/CD Pipeline Notes](notes/ci-cd-pipeline.jpeg)

## 📌 Tools Covered

- **Jenkins** – For automation and orchestration of the pipeline.
- **Maven** – To compile code and run unit tests.
- **SonarQube** – For code quality checks, bugs, vulnerabilities, and code smells.
- **Aqua/Trivy** – For security vulnerability scans.
- **Nexus Repository** – For storing build artifacts.
- **Docker** – For containerization of the application and building Docker images.

## 🔁 Workflow

1. **Issue Tracking:** Jira or similar tools track bugs/features.
2. **Code Push:** Developer writes and pushes code to GitHub.
3. **Jenkins Trigger:** Jenkins pulls the code and triggers the pipeline.
4. **Build Stage (Maven):** Compile and test the application.
5. **Code Quality (SonarQube):** Check for bugs, smells, vulnerabilities.
6. **Security Scan (Trivy):** Scan the app for security issues.
7. **Package (Maven):** Create build artifact.
8. **Store Artifact (Nexus):** Push artifact to Nexus Repository.
9. **Deploy (Docker):** Build Docker image and push to registry.

---

📚 *This is a part of my DevOps learning journey. Stay tuned for more uploads!*

