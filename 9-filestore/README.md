File Store - Default StorageClass


## Step-02: Enable Filestore CSI driver	(If not enabled)
- Go to Kubernetes Engine -> standard-cluster-private-1 -> Details -> Features -> Filestore CSI driver	
- Click on Checkbox **Enable Filestore CSI Driver**
- Click on **SAVE CHANGES**

# Verify Filestore CSI Daemonset in kube-system namespace
kubectl -n kube-system get ds | grep file


# Verify Filestore CSI Daemonset pods in kube-system namespace
kubectl -n kube-system get pods | grep file
Observation: 

## Step-04: Existing Storage Class
- After you enable the Filestore CSI driver, GKE automatically installs the following StorageClasses for provisioning Filestore instances:

# Default Storage Class created as part of FileStore CSI Enablement
kubectl get sc
Observation: Below four storage class will be created by default
standard-rwx
premium-rwx 
enterprise-rwx
enterprise-multishare-rwx

## 01-filestore-pvc.yaml

## 02-write-to-filestore-pod.yaml


# 03-myapp1-deployment.yaml


## 04-loadBalancer-service.yaml


## Step-09: Enable Cloud FileStore API (if not enabled)
- Go to Search -> FileStore -> ENABLE

##  Deploy kube-manifests
# Deploy kube-manifests
kubectl apply -f kube-manifests/

# List Storage Class
kubectl get sc

# List PVC
kubectl get pvc

# List PV
kubectl get pv

# List Pods
kubectl get pods
``` 

## Step-10: Verify GCP Cloud FileStore Instance
- Go to FileStore -> Instances
- Click on **Instance ID: pvc-27cd5c27-0ed0-48d1-bc5f-925adfb8495f**
- **Note:** Instance ID dynamically generated, it can be different in your case starting with pvc-*

## Step-11: Connect to filestore write app Kubernetes pods and Verify
```t
# FileStore write app - Connect to Kubernetes Pod
kubectl exec --stdin --tty <POD-NAME> -- /bin/sh
kubectl exec --stdin --tty filestore-writer-app  -- /bin/sh
cd /data
ls
tail -f myapp1.txt
exit
```

## Step-12: Connect to myapp1 Kubernetes pods and Verify
```t
# List Pods
kubectl get pods 

# myapp1 POD1 - Connect to Kubernetes Pod
kubectl exec --stdin --tty <POD-NAME> -- /bin/sh
kubectl exec --stdin --tty myapp1-deployment-5d469f6478-2kp97 -- /bin/sh
cd /usr/share/nginx/html/filestore
ls
tail -f myapp1.txt
exit

# myapp1 POD2 - Connect to Kubernetes Pod
kubectl exec --stdin --tty <POD-NAME> -- /bin/sh
kubectl exec --stdin --tty myapp1-deployment-5d469f6478-2kp97  -- /bin/sh
cd /usr/share/nginx/html/filestore
ls
tail -f myapp1.txt
exit
```

## Step-13: Access Application
```t
# List Services
kubectl get svc

# Access Application
http://<EXTERNAL-IP-OF-GET-SERVICE-OUTPUT>/filestore/myapp1.txt
http://35.232.145.61/filestore/myapp1.txt
curl http://35.232.145.61/filestore/myapp1.txt
```


## Step-14: Clean-Up
```t
# Delete Kubernetes Objects
kubectl delete -f kube-manifests/

# Verify if FileStore Instance is deleted
Go to -> FileStore -> Instances
```