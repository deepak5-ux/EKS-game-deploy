# 🛠️ SETUP.md (Cluster Setup)

## Prerequisites

* **AWS CLI** installed & configured with credentials.
* **eksctl** installed for cluster management.
* **kubectl** installed for Kubernetes commands.
* **Helm** installed for ALB controller.

## Steps

1. **Create EKS Cluster**

```bash
eksctl create cluster \
  --name demo-cluster \
  --region us-east-1 \
  --fargate
```

2. **Associate IAM OIDC Provider**

```bash
eksctl utils associate-iam-oidc-provider --cluster demo-cluster --approve
```

3. **Create Fargate Profile**

```bash
eksctl create fargateprofile \
  --cluster demo-cluster \
  --region us-east-1 \
  --name alb-sample-app \
  --namespace game-2048
```

4. **Setup IAM Policy for ALB Controller**

```bash
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.11.0/docs/install/iam_policy.json
aws iam create-policy \
  --policy-name AWSLoadBalancerControllerIAMPolicy \
  --policy-document file://iam_policy.json
```

5. **Create Service Account for ALB Controller**

```bash
eksctl create iamserviceaccount \
  --cluster demo-cluster \
  --namespace kube-system \
  --name aws-load-balancer-controller \
  --role-name AmazonEKSLoadBalancerControllerRole \
  --attach-policy-arn=arn:aws:iam::<ACCOUNT_ID>:policy/AWSLoadBalancerControllerIAMPolicy \
  --approve
```

📌 With this structure, your project will look **professional, clear, and recruiter-friendly** on GitHub & LinkedIn.
