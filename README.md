\# ElevateLabs DevOps Internship — Task 5



\## Kubernetes Cluster with Minikube



\---



\## Project Overview



This project demonstrates deploying and managing a containerized application

on a local Kubernetes cluster using Minikube. It covers deployments, services,

configmaps, scaling, and rolling updates.



\---



\## Tools Used



\- Minikube v1.38.1

\- kubectl v1.30.0

\- Docker

\- Kubernetes v1.35.1



\---



\## Project Structure
ElevateLabs-DevOps-Task5/

├── deployment.yaml       # Kubernetes Deployment config

├── service.yaml          # Kubernetes Service config

├── configmap.yaml        # Kubernetes ConfigMap config

└── README.md             # Project documentation
---



\## Kubernetes Objects Used



| Object | Name | Purpose |

|---|---|---|

| Deployment | flask-deployment | Runs 2 replicas of the app |

| Service | flask-service | Exposes app via NodePort 30001 |

| ConfigMap | flask-config | Stores app configuration |



\---



\## Steps Performed



\### 1. Start Minikube Cluster

```bash

minikube start --driver=docker

minikube status

```



\### 2. Apply YAML Files

```bash

kubectl apply -f deployment.yaml

kubectl apply -f service.yaml

kubectl apply -f configmap.yaml

```



\### 3. Verify Pods and Services

```bash

kubectl get nodes

kubectl get pods

kubectl get deployments

kubectl get services

kubectl get configmaps

```



\### 4. Access the Application

```bash

minikube service flask-service --url

```



\### 5. Scale Deployment

```bash

kubectl scale deployment flask-deployment --replicas=4

kubectl scale deployment flask-deployment --replicas=2

```



\### 6. Inspect with describe and logs

```bash

kubectl describe deployment flask-deployment

kubectl describe pods

kubectl logs <pod-name>

```



\### 7. Rolling Update

```bash

kubectl set image deployment/flask-deployment flask-container=gcr.io/google-samples/hello-app:2.0

kubectl rollout status deployment/flask-deployment

kubectl rollout history deployment/flask-deployment

```



\---



\## Kubernetes Interview Q\&A



\*\*1. What is Kubernetes?\*\*

An open-source container orchestration platform that automates deployment,

scaling, and management of containerized applications.



\*\*2. What is the role of kubelet?\*\*

An agent running on each node that ensures containers described in PodSpecs

are running and healthy.



\*\*3. Explain pods, deployments, and services.\*\*

\- Pod: Smallest deployable unit, wraps one or more containers

\- Deployment: Manages pod replicas and rolling updates

\- Service: Stable network endpoint to access pods



\*\*4. How do you scale in Kubernetes?\*\*

```bash

kubectl scale deployment <name> --replicas=<number>

```



\*\*5. What is a namespace?\*\*

A way to divide cluster resources between multiple users or teams.

Default namespace is used when none is specified.



\*\*6. Difference between ClusterIP, NodePort, LoadBalancer?\*\*

\- ClusterIP: Internal only, accessible within cluster

\- NodePort: Exposes app on a static port on each node

\- LoadBalancer: Exposes app via external cloud load balancer



\*\*7. What are ConfigMaps?\*\*

Kubernetes objects that store non-sensitive configuration data as key-value

pairs, decoupled from container images.



\*\*8. How do you perform rolling updates?\*\*

```bash

kubectl set image deployment/<name> <container>=<new-image>

kubectl rollout status deployment/<name>

```

To rollback:

```bash

kubectl rollout undo deployment/<name>

```



\---



\## Key Commands Reference



```bash

minikube start --driver=docker

minikube status

minikube service <service-name> --url



kubectl apply -f <file>.yaml

kubectl get pods

kubectl get deployments

kubectl get services

kubectl get configmaps

kubectl describe deployment <name>

kubectl logs <pod-name>

kubectl scale deployment <name> --replicas=<n>

kubectl rollout status deployment/<name>

kubectl rollout history deployment/<name>

kubectl rollout undo deployment/<name>

```



\---



\## Author



Ashish Vijaybhai Shakoriya

DevOps Internship — ElevateLabs

Task 5: Kubernetes Cluster with Minikube

