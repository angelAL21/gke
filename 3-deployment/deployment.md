
## Kubernetes Deployment - Topics
1. Create Deployment
2. Scale the Deployment
3. Expose Deployment as a Service
4. Update Deployment
5. Rollback Deployment
6. Rolling Restarts
7. Pause & Resume Deployments
8. Canary Deployments (Will be covered at Declarative section of Deployments)


- What is a Deployment?
- What all we can do using Deployment?
- Create a Deployment
- Scale the Deployment
- Expose the Deployment as a Service


# Create Deployment
kubectl create deployment <Deplyment-Name> --image=<Container-Image>

kubectl get deployments
kubectl get deploy 

kubectl describe deployment <deployment-name>


# Verify ReplicaSet
kubectl get rs


# Scale Up the Deployment
kubectl scale --replicas=10 deployment/<Deployment-Name>
kubectl scale --replicas=10 deployment/my-first-deployment 

# Verify Deployment
kubectl get deploy

# Verify ReplicaSet
kubectl get rs

# Verify Pods
kubectl get po

# Scale Down the Deployment
kubectl scale --replicas=2 deployment/my-first-deployment 
kubectl get deploy

# Expose Deployment as a Service
- Expose **Deployment** with a service (LoadBalancer Service) to access the application externally (from internet)

# Expose Deployment as a Service
kubectl expose deployment <Deployment-Name>  --type=LoadBalancer --port=80 --target-port=80 --name=<Service-Name-To-Be-Created>
kubectl expose deployment deploymentangel --type=LoadBalancer --port=80 --target-port=80 --name=my-first-deployment-service

# Get Service Info
kubectl get svc

- **Access the Application using Public IP**

# Access Application
http://<External-IP-from-get-service-output>
curl http://<External-IP-from-get-service-output>