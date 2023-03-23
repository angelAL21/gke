
kubectl apply -f 01-replicaset-definition.yml

# List Replicasets
kubectl get rs
```
- Delete a pod
- ReplicaSet immediately creates the pod. 
```t
# List Pods
kubectl get pods

# Delete Pod
kubectl delete pod <Pod-Name>
```

## Create LoadBalancer Service for ReplicaSet

# Create LoadBalancer Service
kubectl apply -f 02-replicaset-LoadBalancer-service.yml

# List LoadBalancer Service
kubectl get svc

# Access Application
http://<Load-Balancer-Service-IP>
```


## Step-04: Clean-Up Kubernetes ReplicaSet and Service
```t
# Change Directory
cd kube-manifests

# Delete Pod
kubectl delete -f 01-replicaset-definition.yml

# Delete Service
kubectl delete -f  02-replicaset-LoadBalancer-service.yml
```
