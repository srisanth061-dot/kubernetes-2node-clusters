# Kubernetes 2-Node Cluster

## Overview
Set up a 2-node Kubernetes cluster on AWS EC2 using kubeadm with Flannel CNI network plugin. Deployed pods, deployments and services on the cluster.

## Tools Used
- Kubernetes v1.21.2
- kubeadm
- kubectl
- Docker
- Flannel CNI
- AWS EC2

## Cluster Architecture
- Master Node: EC2 t2.medium (Ubuntu 20.04)
- Worker Node: EC2 t2.medium (Ubuntu 20.04)

## Files
- pod.yml - Single pod deployment using nginx
- deployment.yml - Deployment with 3 replicas
- service.yml - NodePort service to expose deployment
- cluster-setup.md - Step by step cluster setup guide

## Commands Used
kubectl apply -f pod.yml
kubectl apply -f deployment.yml
kubectl apply -f service.yml
kubectl get nodes
kubectl get pods
kubectl get services
