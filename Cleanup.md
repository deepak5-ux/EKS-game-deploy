# 🧹 CLEANUP.md (Delete Resources)

To avoid ongoing costs, delete everything once testing is done.

1. **Delete Ingress, Service, Deployment, Namespace**

```bash
kubectl delete -f manifests/
```

2. **Delete Fargate Profile**

```bash
eksctl delete fargateprofile --cluster demo-cluster --name alb-sample-app
```

3. **Delete Cluster**

```bash
eksctl delete cluster --name demo-cluster --region us-east-1
```

⚠️ Note: If you see an error like `deadline surpassed waiting for AWS load balancers`, manually delete ALBs from **EC2 → Load Balancers**.

---
