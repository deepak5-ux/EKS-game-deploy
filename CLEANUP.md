CLEANUP.md (Delete Resources)

To avoid ongoing costs, delete everything once testing is done.

Delete Ingress, Service, Deployment, Namespace
```
kubectl delete -f manifests/
```
Delete Fargate Profile
```

eksctl delete fargateprofile --cluster demo-cluster --name alb-sample-app
```

Delete Cluster
```

eksctl delete cluster --name demo-cluster --region us-east-1
```

⚠️ Note: If you see an error like deadline surpassed waiting for AWS load balancers, manually delete ALBs from EC2 → Load Balancers.

📌 With this structure, your project will look professional, clear, and recruiter-friendly on GitHub & LinkedIn.

