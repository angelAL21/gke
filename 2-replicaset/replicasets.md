Replicasets


- What are ReplicaSets?


kubectl get replicaset
kubectl get rs

kubectl describe rs/<replicaset-name>

kubectl get pods
kubectl describe pod <pod-name>

kubectl get pods -o wide


## Step-03: Expose ReplicaSet as a Service

# Expose ReplicaSet as a Service
kubectl expose rs <ReplicaSet-Name>  --type=LoadBalancer --port=80 --target-port=8080 --name=<Service-Name-To-Be-Created>


kubectl get service
kubectl get svc

# Access Application
http://<External-IP-from-get-service-output>


# To get Pod Name
kubectl get pods

# Delete the Pod
kubectl delete pod <Pod-Name>

# Verify the new pod got created automatically
kubectl get pods   (Verify Age and name of new pod)

# Apply latest changes to ReplicaSet
kubectl replace -f replicaset-demo.yml

# Verify if new pods got created
kubectl get pods -o wide


## Step-06: Delete ReplicaSet & Service
### Step-06-01: Delete ReplicaSet

# Delete ReplicaSet
kubectl delete rs <ReplicaSet-Name>

# Sample Commands
kubectl delete rs/my-helloworld-rs

# Verify if ReplicaSet got deleted
kubectl get rs

# Delete Service
kubectl delete svc <service-name>

# Sample Commands
kubectl delete svc my-helloworld-rs-service


# Verify if Service got deleted
kubectl get svc

