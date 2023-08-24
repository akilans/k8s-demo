# Kubernetes Demo

- This repositorty created to showcase kubernetes basics

### Prerequisites

- Linux Basics
- Docker
- Networking

### K8s Architecture

- ![Kubernetes Architecture](https://github.com/akilans/k8s-demo/blob/main/k8s-arch.png?raw=true)

### Kubernetes Components

- Master Componentes - Etcd, API server, Controller manager and Scheduler
- Worker Components - Docker, Kubelet and Kube proxy

### Setup Kubernetes Cluster

- Locally - [Minikube](https://minikube.sigs.k8s.io/docs/), [Kind](https://kind.sigs.k8s.io/), kubeadm
- Cloud - AWS EKS, Azure AKS, GCP GKE

### Kubernetes Important Resources

- Pod
- Deployment
- Service

### Demo

- Self healing
- Scaling
- Service and Load balancing
- Update deployment

```bash
# Install minikube and start
minikube start
# Install kubectl and check version of k8s cluster
kubectl version --short
# get k8s nodes
kubectl get nodes
# get ns, pods, deployments, services
kubectl get pods
# create a pod
kubectl run nginx-container --image nginx
# delete a pod
kubectl delete pod nginx
# Deployment
kubectl create deployment nginx-dep --image nginx --replicas 3
# delete any pod
# different types of svc ClusterIP inside k8s, NodePort, LoadBalancer
# Access the app
kubectl expose deployment nginx-dep --type NodePort --port 80
# get svc
kubectl get svc
# exec inside a pod
kubectl exec -it $POD_NAME -- bash
# access web ui
# curl http://192.168.49.2:32109/
# clean up svc, dep
# generate yamls
kubectl create deployment nginx-dep --image nginx --replicas 3 --dry-run=client -o yaml > yamls/dep.yaml
# apply
kubectl apply -f yamls/dep.yaml
# check pods, dep
kubectl expose deployment nginx-dep --type NodePort --port 80 --dry-run=client -o yaml > yamls/svc.yaml
# scale
kubectl scale deployment nginx-dep --replicas 1

# service discovery
kubectl create deployment my-apache --image httpd --replicas 2
kubectl expose deployment my-apache --type ClusterIP --port 80
# kubectl get svc
# login into nginx and curl http://my-apache
```
