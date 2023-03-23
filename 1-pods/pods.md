Arquitectura en kubernetes
1. master: kube-apiserver, etcd, kube-scheduler, kube controller manager, cloud controller manager
2. worker node: kubelete, kube-proxy, container runtime

1. Qué es un pod - deep dive - multi-container pods
2. Qué es ReplicaSet
3. Qué es un Deployment
4. Qué es un service
--------

1. crear cluster gke desde 0, para pruebas y deployment
2. conectar con la terminal
3. descargar imagen que está en artifact registry
4. docker images




kubectl get nodes

kubectl get nodes -o wide


- Create a Pod

kubectl run <desired-pod-name> --image <Container-Image> 

# process
1. Kubernetes created a pod
2. Pulled the docker image from docker hub
3. Created the container in the pod
4. Started the container present in the pod


kubectl get pods


kubectl describe pod <Pod-Name>



# To get list of pod names
kubectl get pods

# Delete Pod
kubectl delete pod <Pod-Name>


## Load Balancer Service 


# Create  a Pod
kubectl run <desired-pod-name> --image <Container-Image> 

# Expose Pod as a Service
kubectl expose pod <Pod-Name>  --type=LoadBalancer --port=80 --name=<Service-Name>
kubectl expose pod mypodangel  --type=LoadBalancer --port=80 --name=my-first-service

# Get Service Info
kubectl get service
kubectl get svc

# Describe Service
kubectl describe service my-first-service

# Access Application
http://<External-IP-from-get-service-output>
