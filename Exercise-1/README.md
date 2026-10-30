
@'
# Kubernetes Hands-On Exercise Series

Welcome to Exercise-1 **Kubernetes (K8s) exercises**!

These activities help you understand how Kubernetes runs and manages containerized applications.

## Business Problem (Zepto Example)

Imagine you are a **DevOps Engineer at Zepto**.

The product team built a lightweight **web app** that shows the **storefront and delivery status page** for customers.

Your task: **Deploy this app on Kubernetes** so it is always running, portable, and can be scaled later.

Simulate this using the popular `nginx` container image.

## Exercise 1: Hello Pod

**Goal:** Run your first app inside Kubernetes and access it.

## Pre-Requisites

Install Minikube (one-time setup). You also need **Docker** or a VM driver.

- Linux:
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

- macOS: `brew install minikube`

- Windows (PowerShell as Admin): `choco install minikube`

- WSL:
```bash
sudo apt-get update -y
sudo apt-get install -y curl apt-transport-https
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

## Steps: Deploy Nginx as a Pod

1. Start a local cluster:
```bash
minikube start
```

2. Create the Pod:
```bash
kubectl run hello-k8s --image=nginx --port=80
```

3. Verify it is running:
```bash
kubectl get pods
```

4. Expose it as a Service:
```bash
kubectl expose pod hello-k8s --type=NodePort --port=80
```

5. Open the app:
```bash
minikube service hello-k8s
```

You should see the Nginx welcome page. Congratulations, you just deployed your first container in Kubernetes!

### Declarative version

```bash
kubectl apply -f pod.yaml -f service.yaml
```

## System Internal Details

<p align="center">
  <img src="../Images/k8s-exercise-1.jpg" alt="Kubernetes Internals" width="1000"/>
</p>
'@ | Set-Content -Path "Exercise-1/README.md" -Encoding utf8
