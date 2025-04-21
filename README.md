# 🚀 Deploy a Two-Tier Flask App on Kubernetes

This repository provides the Kubernetes YAML files to deploy a **Two-Tier Flask Web Application** with a **MySQL database** backend on a `kubeadm` Kubernetes cluster.

---

## 📦 Prerequisites

Before deploying this app, you must set up a Kubernetes cluster using `kubeadm`.

👉 **Follow the Kubernetes setup here:**  
🔗 [Kubernetes Installation using Kubeadm](https://github.com/rsharmaofficial/Kubernetes-installation)

---

## 💠 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/rsharmaofficial/2-tier-flask
```

---

### 2. Navigate to Kubernetes Manifests

```bash
cd 2-tier-flask/k8s
```

---

### 3. Apply the Kubernetes YAML Files

Run the following commands to deploy your app components in the correct order:

#### 📁 Persistent Volume & Claim

```bash
kubectl apply -f persistent-volume.yml
kubectl apply -f persistent-volume-claim.yml
```

#### 🐬 MySQL Deployment and Service

```bash
kubectl apply -f mysql-deployment.yml
kubectl apply -f mysql-deployment-svc.yml
```

#### 🌐 Flask App Deployment and Service

```bash
kubectl apply -f twotier-deployment.yml
kubectl apply -f twotier-deployment-svc.yml
```

---

## 📸 Screenshots

| EC2 Initialization | MySQL Pod Running | Flask App Running |
|--------------------|-------------------|--------------------|
| ![EC2 Init](./Screenshot%202025-04-19%20003816.png) | ![MySQL Deployment](./Screenshot%202025-04-19%20003345.png) | ![App Pod](./Screenshot%202025-04-19%20003403.png) |
| ![PVC Bound](./Screenshot%202025-04-19%20003416.png) | ![Pods List](./Screenshot%202025-04-19%20003428.png) | ![Service Created](./Screenshot%202025-04-19%20003441.png) |

> 🖼️ Make sure these images are stored in the root of your repo for proper rendering.

---

## 📡 Accessing the Application

After all services are up and running, find the external IP or NodePort to access the app:

```bash
kubectl get svc
```

Then open the exposed IP address in your browser.

---

## 🙌 Author

Made with ❤️ by [Rishabh Sharma](https://github.com/rsharmaofficial)

---

## 📃 License

This project is open-source and available under the [MIT License](LICENSE).

