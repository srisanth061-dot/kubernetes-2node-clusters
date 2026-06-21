# Kubernetes Cluster Setup Guide

## Infrastructure
- 2 AWS EC2 instances (t2.medium)
- Master Node: 1 instance
- Worker Node: 1 instance
- OS: Ubuntu 20.04
- Kubernetes Version: v1.21.2

## Steps to Set Up Cluster

### On Both Nodes
1. Update system packages
2. Install Docker
3. Install kubeadm, kubelet, kubectl
4. Disable swap

### On Master Node
1. Initialize cluster using kubeadm
2. Set up kubeconfig
3. Install Flannel CNI network plugin

### On Worker Node
1. Join cluster using token from master node

## Commands Used

### Initialize Master
kubeadm init --pod-network-cidr=10.244.0.0/16

### Setup kubeconfig
mkdir -p $HOME/.kube
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config

### Install Flannel CNI
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

### Join Worker Node
kubeadm join <master-ip>:6443 --token <token> --discovery-token-ca-cert-hash <hash>

### Verify Cluster
kubectl get nodes
kubectl get pods --all-namespaces
