

# Create LoadBalancer Service
kubectl apply -f 02-deployment-LoadBalancer-service.yml

# List Service
kubectl get svc

# Get Public IP
kubectl get nodes -o wide

# Access Application
http://<Load-Balancer-Service-IP>

cd kube-manifests

# Delete Deployment
kubectl delete -f 01-deployment-definition.yml

# Delete LoadBalancer Service
kubectl delete -f 02-deployment-LoadBalancer-service.yml
```


## API References
- [Deployment](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.26/#deployment-v1-apps)
