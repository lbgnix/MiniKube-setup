# MiniKube-setup
minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away: minikube start

Lets follow the step by step process to setup minikube on local setup- 
Setup and Configure Minikube on a Virtual Machine
In this Practical you will setup and configure MiniKube on an Ubuntu VM. MiniKube is a tool that makes it easy to run Kubernetes locally and runs a single-node Kubernetes cluster.


CMD to setup Minikube on ubuntu System :- 

```
Step 1:
sudo -i
rm /var/lib/apt/lists/lock
rm /var/cache/apt/archives/lock 
rm /var/lib/dpkg/lock
cd ~/labs/module5
chmod +x install-minikube.sh
./install-minikube.sh
minikube --help
kubectl run nginx --image=nginx --port=80
kubectl expose deployment nginx --type=NodePort
kubectl get deployment
kubectl get service
curl $(minikube service nginx --url)
kubectl delete service nginx
kubectl delete deployment nginx
```
Step 2:

1. Health probes
```
kubectl apply -f  liveness-probe.yaml
kubectl get pods
kubectl describe po liveness-probe
kubectl logs liveness-probe --previous
kubectl get replicasets
kubectl delete pod liveness-probe
```
2. Replica Sets
```
kubectl create -f  nginx-rc.yaml
kubectl get pods --show-labels
kubectl get replicaset
kubectl delete pod <<pod-name>>
kubectl get pods --show-labels
kubectl label pod <<pod-name>> app=debugging --overwrite=true
kubectl get pods --show-labels
kubectl get pods --show-labels -l app=webapp
kubectl delete replicaset nginx-replica
kubectl get pods
kubectl get pods --show-labels
kubectl delete pods -l app=debugging
```
3. Deployments
```
kubectl create -f nginx-deployment.yaml
kubectl get deployment
kubectl get pods --show-labels
kubectl describe deployment nginx-deployment
kubectl apply -f nginx-deployment-updated.yaml
kubectl get pods --show-labels
kubectl describe deployment nginx-deployment
```
