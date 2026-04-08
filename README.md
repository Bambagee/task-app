<p align="center">
  <img width="126" height="126" alt="image" src="https://github.com/user-attachments/assets/9d988702-0739-44f1-97cb-57fa2d2dc38b" />
</p>

<h1 align="center">TASK APP</h1>

<p align="center">
  A full-stack task management application built incrementally over 12 weeks,<br/>
  demonstrating real-world DevOps and Cloud Engineering workflows.
</p>

---

## 🚀 Full Pipeline

---

## 🔋 Technologies Used

### Core
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

### CI/CD
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)

### Containers & Infrastructure
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)

### Cloud
![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)

### Monitoring
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)

---

## 📅 Weekly Progress

| Week | Topic | What Was Done |
|------|-------|---------------|
| 1 | Project Setup | Built Node.js backend + HTML frontend running locally |
| 2 | Git & GitHub | Pushed code to GitHub for version control |
| 3 | GitHub Actions | Auto-test pipeline on every push |
| 4 | Jenkins | Enterprise CI/CD pipeline on a VM |
| 5 | Docker | Containerized app and pushed images to Docker Hub |
| 6 | Terraform | Created Azure VM infrastructure as code |
| 7/8 | Kubernetes | Separated frontend/backend, deployed to K3s, automated via Jenkins |
| 9 | Monitoring | Prometheus + Grafana monitoring inside Kubernetes |

---

## 🏗️ Architecture

---

## ⚙️ Infrastructure (Terraform)

All Azure infrastructure is managed as code:

- ✅ Virtual Machine (`Standard_B2s`)
- ✅ Virtual Network + Subnet
- ✅ Network Security Group (ports: 22, 80, 3000, 8080, 30007, 32000)
- ✅ Public IP (Static)
- ✅ SSH Key Authentication

---

## 🐳 Docker Images

| Service | Image |
|---------|-------|
| Frontend | `bambadra/docker-task-app_repo-frontend:latest` |
| Backend | `bambadra/docker-task-app_repo-backend:latest` |

---

## ☸️ Kubernetes Services

| Service | Type | Port |
|---------|------|------|
| frontend-service | NodePort | 30007 |
| backend-service | ClusterIP | 3000 |
| monitoring-grafana | NodePort | 32000 |

---

## 📊 Monitoring

Prometheus and Grafana run inside Kubernetes and monitor:

- CPU and memory usage per pod
- Node resource consumption
- Network traffic
- Pod health and restarts

Access Grafana: `http://YOUR-VM-IP:32000`

---

## 🔁 CI/CD Pipeline (Jenkins)

Every `git push` triggers:

1. Jenkins pulls latest code from GitHub
2. Builds new Docker images (frontend + backend)
3. Pushes images to Docker Hub with build number tag
4. Updates Kubernetes deployments with new images
5. Kubernetes performs rolling update with zero downtime

---

## 📁 Project Structure

---

## 🚦 Getting Started

**Clone the repo:**
```bash
git clone https://github.com/Bambagee/task-app.git
cd task-app
```

**Run locally:**
```bash
cd backend
npm install
node server.js
```

**Deploy infrastructure:**
```bash
cd terraform-ec2
terraform init
terraform apply
```

**Deploy to Kubernetes:**
```bash
kubectl apply -f k8s/
```

---

## 📌 Key Learnings

- How to separate frontend and backend into independent deployable services
- How Docker images work and why they are called images
- The difference between NodePort, ClusterIP and LoadBalancer services
- How Jenkins automates the entire build and deploy process
- How Prometheus and Grafana provide real-time observability
- How Terraform manages cloud infrastructure as code

---

<p align="center">Built with ❤️ as part of a 12-week DevOps learning journey</p>
