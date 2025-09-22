# IAM Configuration for EKS 2048 Project

This folder contains IAM configurations for the **Amazon EKS 2048 Game Deployment Project**.

---

## 📂 Files

* **iam\_policy.json** → Custom IAM policy required for the ALB Ingress Controller.
* **iam\_serviceaccount.yaml** → eksctl configuration to create a Kubernetes Service Account with IAM Role for Service Account (IRSA).

---

## ⚙️ Setup Steps

### 1. Associate OIDC Provider

Your EKS cluster must have an OIDC provider associated to use IRSA:

```bash
eksctl utils associate-iam-oidc-provider --cluster demo-cluster --approve
```

### 2. Create IAM Policy

Apply the IAM policy for ALB Ingress Controller:

```bash
aws iam create-policy \
  --policy-name ALBIngressControllerIAMPolicy \
  --policy-document file://iam/iam_policy.json
```

### 3. Create IAM Service Account

Use eksctl to create the service account and bind it to the IAM policy:

```bash
eksctl create iamserviceaccount \
  --config-file=iam/iam_serviceaccount.yaml \
  --approve
```

This will create a Kubernetes Service Account (`alb-ingress-controller`) in the `kube-system` namespace, linked to the IAM role.

---

## 🧹 Cleanup

To avoid leaving unused IAM resources:

```bash
# Delete IAM service account
eksctl delete iamserviceaccount \
  --cluster demo-cluster \
  --name alb-ingress-controller \
  --namespace kube-system

# Delete IAM policy
aws iam delete-policy \
  --policy-arn arn:aws:iam::<account-id>:policy/ALBIngressControllerIAMPolicy
```

---

✅ With this setup, your ALB Ingress Controller has the required permissions via IRSA instead of attaching permissions at the node level — following AWS best practices.

