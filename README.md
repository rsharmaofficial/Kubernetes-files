# Kubernetes Two-Tier Flask App Deployment Guide

## Overview
This project demonstrates how to deploy a **two-tier architecture** using Kubernetes, consisting of a **Flask web application** connected to a **MySQL database**. You will learn how to:

- Create deployments and services in Kubernetes.
- Connect a web app to a MySQL database.
- Scale the application.
- Set up persistent storage for MySQL.

---

## 🛠️ Prerequisites

- A running Kubernetes cluster (preferably set up with `kubeadm`).
- `kubectl` installed and configured.
- Basic knowledge of Kubernetes.
- Docker images already available on Docker Hub.

> You can refer to this [Kubernetes installation repo](https://github.com/rsharmaofficial/Kubernetes-installation) to set up your cluster.

---

## 📁 Project Structure

```
.
├── k8s
│   ├── mysql-deployment.yml
│   ├── mysql-deployment-svc.yml
│   ├── persistent-volume.yml
│   ├── persistent-volume-claim.yml
│   ├── twotier-deployment.yml
│   └── twotier-deployment-svc.yml
└── README.md
```

---

## 🚀 Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/rsharmaofficial/2-tier-flask
cd 2-tier-flask/k8s
```

### 2. Apply the Kubernetes YAML Files

#### Create Persistent Volume and Claim for MySQL
```bash
kubectl apply -f persistent-volume.yml
kubectl apply -f persistent-volume-claim.yml
```

#### Deploy the MySQL Database
```bash
kubectl apply -f mysql-deployment.yml
kubectl apply -f mysql-deployment-svc.yml
```

#### Deploy the Flask Application
```bash
kubectl apply -f twotier-deployment.yml
kubectl apply -f twotier-deployment-svc.yml
```

---

## 📦 YAML Breakdown

### twotier-deployment.yml
- Deploys a Flask container using Docker image `trainwithshubham/two-tier-flask-app`.
- Environment variables connect it to the MySQL service.
- You can scale it using:
```bash
kubectl scale deployment flask-app --replicas=3
```

### twotier-deployment-svc.yml
- Exposes the Flask app on `NodePort` for external access.
- You can get the port using:
```bash
kubectl get svc
```

### mysql-deployment.yml
- Creates a pod running MySQL.
- Connects the database to persistent storage.
- Initializes with environment variables.

### mysql-deployment-svc.yml
- Exposes MySQL as a `ClusterIP` service so Flask can connect to it inside the cluster.

### persistent-volume.yml & persistent-volume-claim.yml
- Ensure MySQL data persists even after pod restarts or rescheduling.

---
---

## ✅ Validation & Access

- Confirm everything is running:
```bash
kubectl get all
```
- Access the Flask app using your EC2 public IP and the `NodePort` assigned.

---

## 🧠 Concepts Covered

- Kubernetes Deployments, Services, PV/PVC.
- Docker image usage in K8s.
- Two-tier architecture (Web + DB).
- Stateful application deployment.

---

## 🤝 Contributing
Feel free to fork and contribute. Raise issues if anything breaks!

---

## 👨‍💻 Author
**Rishabh Sharma**

GitHub: [@rsharmaofficial](https://github.com/rsharmaofficial)

---

## 📄 License
This project is licensed under the MIT License.

---

Happy Deploying! 🚀

