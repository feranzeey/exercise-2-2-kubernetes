#  Kubernetes Application Deployment - Exercise 2.2

##  Project Overview

This project demonstrates a **multi-tier Kubernetes deployment** using Minikube. It simulates a real-world production environment with frontend, API, and database layers deployed on Kubernetes using YAML manifests.

The goal of this exercise is to understand how to deploy, manage, and scale applications using Kubernetes concepts such as Deployments, Services, Namespaces, and Autoscaling.

---

##  Technologies Used

* Kubernetes (Minikube)
* kubectl
* Docker
* YAML (Kubernetes manifests)
* Git & GitHub

---

##  Project Structure

```
exercise-2-2-kubernetes/
│
├── namespace.yaml
├── frontend-deployment.yaml
├── frontend-service.yaml
├── api-deployment.yaml
├── api-service.yaml
├── database-deployment.yaml
├── database-service.yaml
├── hpa.yaml
├── networkpolicy.yaml
```

---

##  Architecture

The system is built with 3 layers:

* **Frontend Layer** → Exposed using NodePort service
* **API Layer** → Internal ClusterIP service
* **Database Layer** → PostgreSQL deployment

---

##  Setup Instructions

### 1. Start Minikube Cluster

```bash
minikube start --driver=docker
```

---

### 2. Enable Addons

```bash
minikube addons enable metrics-server
minikube addons enable dashboard
```

---

### 3. Apply All Kubernetes Resources

```bash
kubectl apply -f .
```

---

### 4. Verify Deployment

```bash
kubectl get nodes
kubectl get pods -n production
kubectl get svc -n production
kubectl get deployments -n production
```

---

##  Features Implemented

* ✅ Multi-tier architecture (Frontend, API, Database)
* ✅ Kubernetes Namespace isolation
* ✅ Deployment of containers using YAML
* ✅ Service discovery using ClusterIP & NodePort
* ✅ Horizontal Pod Autoscaling (HPA)
* ✅ Resource requests and limits
* ✅ Network policy configuration
* ✅ Metrics server enabled for monitoring

---

##  Scaling

The frontend deployment is configured with autoscaling:

* Minimum replicas: 2
* Maximum replicas: 5
* CPU utilization target: 50%

---

##  Security

* Network policies implemented to control traffic flow
* Namespace isolation for environment separation
* Resource limits applied to prevent overconsumption

---

##  How to Access Application

If using Minikube:

```bash
minikube service frontend -n production
```

This will open the application in your browser.

---

##  Learning Outcomes

* Kubernetes architecture understanding
* Deploying multi-container applications
* Managing services and networking
* Implementing autoscaling
* Working with real-world DevOps workflows

---

##  Author

**Oluwaferanmi Dada**

---

## Notes

This project is part of a DevOps training exercise focusing on CI/CD and Kubernetes deployment practices.
