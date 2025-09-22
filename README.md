# 📘 Amazon EKS 2048 Game Project

This repository documents the complete workflow of deploying the **2048 game application** on **Amazon Elastic Kubernetes Service (EKS)** using **AWS Fargate** and an **Application Load Balancer (ALB)**. The project demonstrates practical DevOps skills in Kubernetes, AWS, and Infrastructure as Code.

---

## 📂 Repository Structure

```
eks-2048-project/
│
├── README.md                   # Main project overview & summary
├── SETUP.md                    # AWS & EKS setup guide
├── DEPLOYMENT.md               # Deploying 2048 app on EKS
├── CLEANUP.md                  # Deleting all resources to avoid billing
│
├── manifests/                  # Kubernetes YAML files
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
│
├── iam/                        # IAM policies & service accounts
│   ├── iam_policy.json
│   └── iam_serviceaccount.yaml
│
│
│
└── .gitignore                  # Ignore unnecessary files
```

---

# 📖 README.md (Main Overview)

## 🎯 Project Goal

The goal of this project is to demonstrate **how to deploy a containerized application (2048 game)** onto **Amazon EKS** using managed Kubernetes features like Fargate and exposing it with an ALB Ingress.

---

## 🚀 Key Features

* **Amazon EKS**: Managed Kubernetes cluster.
* **AWS Fargate**: Serverless compute for running pods.
* **IAM Roles & OIDC**: Secure authentication for Kubernetes services.
* **AWS ALB Controller**: External access to application.
* **Infrastructure as Code**: eksctl + YAML manifests.

---

## 📊 Architecture Diagram

![EKS Architecture](architecture/eks-2048.png)

---

## 📚 Documentation Links

* [Setup.md](./Setup.md) → Cluster creation, IAM, tools setup.
* [Deployment.md](./Deployment.md) → App deployment with manifests.
* [Cleanup.md](./Cleanup.md) → Safe deletion of cluster & resources.
