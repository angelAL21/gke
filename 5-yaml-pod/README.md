

# Create Pod
kubectl create -f 01-pod-definition.yml


# List Pods
kubectl get pods


# Create Service
kubectl apply -f 02-pod-LoadBalancer-service.yml

# List Service
kubectl get svc

cd kube-manifests

# Delete Pod
kubectl delete -f 01-pod-definition.yml

# Delete Service
kubectl delete -f  02-pod-LoadBalancer-service.yml
```
