
- GKE Private Cluster 
- GCP Cloud SQL with Private IP 


## Step-02: Create Private Service Connection to Google Managed Services from our VPC Network
## Step-02-01: Create ALLOCATED IP RANGES FOR SERVICES
- Go to VPC Networks -> default -> PRIVATE SERVICE CONNECTION -> ALLOCATED IP RANGES FOR SERVICES
- Click on **ALLOCATE IP RANGE**
- **Name:** google-managed-services-default  (google-managed-services-<VPC-NAME>)  
- **IP Range:** Automatic
- **Prefix Length:** 16
- Click on **ALLOCATE** 

## Step-02-02: Create PRIVATE CONNECTIONS TO SERVICES
- Delete existing connection if any present `servicenetworking-googleapis-com`
- Click on **CREATE CONNECTION**
- **Connected Service Provider:** Google Cloud Platform
- **Connection Name:** servicenetworking-googleapis-com (DEFAULT POPULATED CANNOT CHANGE)
- **Assigned IP Allocation:** google-managed-services-default  
- Click on **CONNECT**

## Step-03: Create Google Cloud SQL MySQL Instance
- Go to SQL -> Choose MySQL
- **Instance ID:** db-private-instance
- **Password:** password 


## Step-04: Create DB Schema webappdb 
- Go to SQL ->  ums-db-public-instance -> Databases -> **CREATE DATABASE**
- **Database Name:** webappdb
- **Character set:** utf8
- **Collation:** Default collation
- Click on **CREATE**


## Step-05: 01-MySQL-externalName-Service.yaml


 ## 02-Kubernetes-Secrets.yaml


# Base64 of KalyanReddy13


## Step-07: 03-UserMgmtWebApp-Deployment.yaml

## Step-08: 04-UserMgmtWebApp-LoadBalancer-Service.yaml


## Step-09: Deploy kube-manifests
```t
# Deploy Kubernetes Manifests
kubectl apply -f kube-manifests/

# List Deployments
kubectl get deploy

# List Pods
kubectl get pods

# List Services
kubectl get svc

# Verify Pod Logs
kubectl get pods
kubectl logs -f <USERMGMT-POD-NAME>



## Step-10: Access Application

# List Services


## Step-11: Connect to MySQL DB (Cloud SQL) from GKE Cluster using kubectl

kubectl run -it --rm --image=mysql:8.0 --restart=Never mysql-client -- mysql -h <Kubernetes-ExternalName-Service> -u <USER_NAME> -p<PASSWORD>

# MySQL Client 8.0: Replace External Name Service, Username and Password
kubectl run -it --rm --image=mysql:8.0 --restart=Never mysql-client -- mysql -h mysql-externalname-service -u root password


## Step-12: Create New user admin102 and verify in Cloud SQL MySQL webappdb


## Step-13: Clean-Up

# Delete Kubernetes Objects
kubectl delete -f kube-manifests/
