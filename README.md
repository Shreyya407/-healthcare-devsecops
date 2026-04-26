## Secure DevSecOps Implementation in Healthcare Systems

---

## Objective

To implement a secure DevSecOps pipeline for a healthcare application by integrating CI/CD, containerization, security testing, and monitoring.

---

## Introduction

DevSecOps integrates security into every stage of the software development lifecycle. In healthcare systems, protecting patient data (PHI – Protected Health Information) is critical. This experiment demonstrates how security practices can be embedded into development, testing, and deployment processes.

---

## Tools Used

Jenkins – Continuous Integration and Deployment
Docker – Containerization
Kubernetes – Deployment (optional/demo)
SonarQube – Static Code Analysis
Trivy – Container Security Scanning
OWASP ZAP – Dynamic Application Security Testing
Prometheus and Grafana – Monitoring
GitHub – Version Control

---

## Prerequisites

AWS account
EC2 instance (Ubuntu)
GitHub repository
Basic knowledge of Docker and Jenkins

---

## Procedure

### Step 1: Setup Infrastructure

An EC2 instance was launched on AWS with required ports open.

---

### Step 2: Install Required Tools

The following commands were used to install Docker and Git:

```
sudo apt update
sudo apt install docker.io git -y
```

Jenkins and other tools were installed for pipeline creation.

---

### Step 3: Application Setup

A simple Node.js application was created:

```
console.log("Hello Healthcare App");
```

---

### Step 4: Static Code Analysis (SAST)

SonarQube was integrated into the Jenkins pipeline to analyze code and detect vulnerabilities.

---

### Step 5: Dependency Scanning (SCA)

Dependencies were scanned using:

```
npm audit
```

---

### Step 6: Docker Image Creation

A Dockerfile was created:

```
FROM node:18-alpine
COPY . .
CMD ["node", "app.js"]
```

The image was built using:

```
docker build -t healthcare-app .
```

---

### Step 7: Container Security Scan

The Docker image was scanned using Trivy:

```
trivy image healthcare-app
```

---

### Step 8: Jenkins Pipeline

A pipeline was created in Jenkins to automate the process:

```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { sh 'docker build -t app .' }
        }
        stage('Security Scan') {
            steps { sh 'trivy image app' }
        }
        stage('Deploy') {
            steps { echo 'Deployment simulated' }
        }
    }
}
```

---

### Step 9: Deployment

The application was deployed using Docker. Kubernetes deployment was simulated for demonstration purposes.

---

### Step 10: Monitoring

Prometheus and Grafana were used to monitor system performance and visualize metrics such as CPU usage and system activity.

---

## Expected Output

The pipeline executes successfully.
The application is containerized and runs correctly.
Security vulnerabilities are detected during scanning.
Monitoring dashboards display system metrics.

---

## Result

A secure DevSecOps pipeline was successfully implemented for a healthcare application. The system ensures code security, container security, and automated deployment with monitoring support.

---
