# Kubernetes

## Projects
- Hello World REST API
- 2 Microservices - Currency Exchange and Currency Conversion

## Steps
- Step 01 - Getting Started with Docker, Kubernetes and Google Kubernetes Engine
- Step 02 - Creating Google Cloud Account
- Step 03 - Creating Kubernetes Cluster with Google Kubernete Engine (GKE)
- Step 04 - Review Kubernetes Cluster and Learn Few Fun Facts about Kubernetes
- Step 05 - Deploy Your First Spring Boot Application to Kubernetes Cluster
- Step 06 - Quick Look at Kubernetes Concepts - Pods, Replica Sets and Deployment
- Step 07 - Understanding Pods in Kubernetes
- Step 08 - Understanding ReplicaSets in Kubernetes
- Step 09 - Understanding Deployment in Kubernetes
- Step 10 - Quick Review of Kubernetes Concepts - Pods, Replica Sets and Deployment
- Step 11 - Understanding Services in Kubernetes
- Step 12 - Quick Review of GKE on Google Cloud Console 
- Step 13 - Understanding Kubernetes Architecture - Master Node and Nodes
- Step 14 - Understand Google Cloud Regions and Zones
- Step 15 - Installing GCloud
- Step 16 - Installing Kubectl 
- Step 17 - Understand Kubernetes Rollouts
- Step 18 - Generate Kubernetes YAML Configuration for Deployment and Service
- Step 19 - Understand and Improve Kubernetes YAML Configuration
- Step 20 - Using Kubernetes YAML Configuration to Create Resources
- Step 21 - Understanding Kubernetes YAML Configuration - Labels and Selectors
- Step 22 - Quick Fix to reduce release downtime with minReadySeconds
- Step 23 - Understanding Replica Sets in Depth - Using Kubernetes YAML Config
- Step 24 - Configure Multiple Kubernetes Deployments with One Service
- Step 25 - Playing with Kubernetes Commands - Top Node and Pod
- Step 26 - Delete Hello World Deployments
- Step 27 - Quick Introduction to Microservices - CE and CC
- Step 28 - Deploy Microservices to Kubernetes
- Step 29 - Understand Environment Variables created by Kubernetes for Services
- Step 30 - Microservices and Kubernetes Service Discovery - Part 1
- Step 31 - Microservices and Kubernetes Service Discovery - Part 2 DNS
- Step 32 - Microservices Centralized Configuration with Kubernetes ConfigMaps
- Step 33 - Simplify Microservices with Kubernetes Ingress - Part 1
- Step 34 - Simplify Microservices with Kubernetes Ingress - Part 2
- Step 35 - Delete Kubernetes Clusters


## Commands

```
docker run -p 8080:8080 in28min/hello-world-rest-api:0.0.1.RELEASE

```
## Step 05
```

kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080  # This is the service

```
## Step 06
```
kubectl get events
kubectl get pods
kubectl get replicaset
kubectl get deployment
kubectl get service

```
## Step 07
```
kubectl get pods -o wide
kubectl explain pods
kubectl describe pod hello-world-rest-api-687d9c7bc7-tw5rk

```
## Step 08
```
kubectl get replicasets
kubectl get replicaset
kubectl get rs
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-687d9c7bc7-tw5rk
kubectl scale deployment hello-world-rest-api --replicas=3
kubectl get pods
kubectl get replicaset
kubectl get events
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl explain replicaset

```
## Step 09
```
kubectl get rs
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST    # This image has an error
kubectl get pods
kubectl describe pod (pod id)
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE

```
## Step 10
```
# Only recall

```
## Step 11
```
kubectl get pods -o wide
kubectl delete pod (pod id)
kubectl get service

```
## Step 12
```
# following the UI

```
## Step 13
```
# Concepts of Master Node and Worker Nodes
kubectl get componentstatuses

```
## Step 14
```
# Regions and zones

```
## Step 15
```
# Installation of gcloud on linux
https://cloud.google.com/sdk/docs/install#linux
gcloud init

```
## Step 16
```
# kubectl installation on linux
https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

```
## Step 17
```
kubectl rollout history deployment hello-world-rest-api
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.3.RELEASE --record=true
kubectl rollout undo deployment hello-world-rest-api --to-revision=1
kubectl logs (pod id)
kubectl logs -f (pod id)

```
## Step 18
```
kubectl get deployment hello-world-rest-api -o yaml
kubectl get deployment hello-world-rest-api -o yaml > deployment.yaml
kubectl get service hello-world-rest-api -o yaml > service.yaml
kubectl apply -f deployment.yaml

```
## Step 19
```
kubectl get all
kubectl get all -o wide
kubectl delete all -l app=hello-world-rest-api

```
## Step 20
```
kubectl apply -f /usr/local/src/Udemy/devops-master-class/kubernetes/01-hello-world-rest-api/backup/02-deployment-cleanedup.yaml
kubectl get svc --watch
kubectl diff -f deployment.yaml
# change the replica and apply again
kubectl apply -f /usr/local/src/Udemy/devops-master-class/kubernetes/01-hello-world-rest-api/backup/02-deployment-cleanedup.yaml

```
## Step 21
```
# Understanding meta-data structure of YAML

```
## Step 22
```
# Modifying the minReadySeconds parameter to avoid downtime - 45 seconds
kubectl apply -f /usr/local/src/Udemy/devops-master-class/kubernetes/01-hello-world-rest-api/backup/02-deployment-cleanedup.yaml

```
## Step 23
```
# ReplicaSet can not handle releases, its only worry about pods
kubectl get all -o wide
kubectl delete all -l app=hello-world-rest-api
kubectl get all
kubectl apply -f /usr/local/src/Udemy/devops-master-class/kubernetes/01-hello-world-rest-api/backup/03-replicaset.yaml
watch curl http://34.68.84.18:8080/hello-world
# Modify to version 2 and apply again
kubectl get pods
kubectl delete pod (por id) # its the only way to update

```
## Step 24
```
kubectl get all -o wide
kubectl delete deployment hello-world-rest-api
kubectl get all -o wide
kubectl delete replicaset.apps/hello-world-rest-api-797dd4b5dc



kubectl autoscale deployment hello-world-rest-api --max=10 --cpu-percent=70
kubectl edit deployment hello-world-rest-api #minReadySeconds: 15

gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-a --project solid-course-258105
kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get pods --all-namespaces

kubectl get rs
kubectl get rs -o wide
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
kubectl get rs -o wide
kubectl get pods
kubectl get events --sort-by=.metadata.creationTimestamp

kubectl set image deployment hello-world-rest-api hello-world-rest-api=in28min/hello-world-rest-api:0.0.2.RELEASE
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-n6c7l
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-8bhdt

kubectl get componentstatuses
kubectl get pods --all-namespaces

gcloud auth login
kubectl version
gcloud container clusters get-credentials in28minutes-cluster --zone us-central1-a --project solid-course-258105


kubectl get pods --all-namespaces
kubectl get pods --all-namespaces -l app=hello-world-rest-api
kubectl get services --all-namespaces
kubectl get services --all-namespaces --sort-by=.spec.type
kubectl get services --all-namespaces --sort-by=.metadata.name
kubectl cluster-info
kubectl cluster-info dump
kubectl top node
kubectl top pod
kubectl get services
kubectl get svc
kubectl get ev
kubectl get rs
kubectl get ns
kubectl get nodes
kubectl get no
kubectl get pods
kubectl get po



kubectl apply -f deployment.yaml 
kubectl apply -f ../currency-conversion/deployment.yaml 
```
