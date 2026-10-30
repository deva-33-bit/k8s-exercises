# DevOps Lab Exercises Repository

This repository contains hands-on DevOps lab exercises covering containerization, container orchestration, Docker networking, container security, CI/CD automation, and real-time monitoring systems.

**Author / Maintainer:** [Devendra (deva-33-bit)](https://github.com/deva-33-bit)  
**Repository:** [k8s-exercises](https://github.com/deva-33-bit/k8s-exercises)

---

## Exercise Catalog

| # | Exercise Folder | Key Technologies | Description |
|---|---|---|---|
| **01** | [Exercise-1](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-1) | Kubernetes, Minikube, Nginx | Create and deploy a Kubernetes Pod running Nginx and expose it using a NodePort Service. |
| **02** | [Exercise-2](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-2) | Kubernetes, Minikube, Docker, Python, Flask | Build a Python Flask application, containerize it with Docker, and deploy it on Minikube. |
| **03** | [Exercise-3](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-3) | Kubernetes, ReplicaSets, Flask, Docker | Implement application scaling and high availability using Kubernetes ReplicaSets. |
| **04** | [Exercise-4](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-4) | Docker, Bridge Networks, Flask, MySQL, Redis | Configure multi-container networking using custom Docker bridge networks and container communication. |
| **05** | [Exercise-5](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-5) | Docker Security, AppArmor, Python | Explore Docker container security using AppArmor profiles and the Python Docker SDK. |
| **06** | [Exercise-6](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-6) | Prometheus, Grafana, Python, Monitoring | Build a real-time monitoring system with custom metrics, Prometheus monitoring, Grafana dashboards, and alerting. |
| **07** | [Exercise-7](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-7) | Jenkins, Docker, CI/CD | Understand Continuous Integration and configure Jenkins using Docker. |
| **08** | [Exercise-8](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-8) | Jenkins, GitHub, Freestyle Jobs | Create and execute a Jenkins Freestyle Job integrated with GitHub. |
| **09** | [Exercise-9](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-9) | Jenkins Pipeline, Groovy, Flask, Python | Build a multi-stage Jenkins CI/CD pipeline for a Python Flask application. |
| **10** | [Exercise-10](https://github.com/deva-33-bit/k8s-exercises/tree/main/Exercise-10) | Minikube Multi-Node, Kubernetes, Flask, Pod Anti-Affinity | Configure a multi-node Minikube cluster and deploy applications using Kubernetes scheduling and Pod Anti-Affinity. |

---

## Technologies and Tools

- **Containerization:** Docker
- **Container Orchestration:** Kubernetes, Minikube, kubectl
- **CI/CD Automation:** Jenkins
- **Monitoring and Visualization:** Prometheus, Grafana
- **Application Development:** Python, Flask
- **Databases and Caching:** MySQL, Redis
- **Container Security:** AppArmor
- **Version Control:** Git, GitHub

---

## Repository Structure

```text
k8s-exercises/
│
├── Exercise-1/
├── Exercise-2/
├── Exercise-3/
├── Exercise-4/
├── Exercise-5/
├── Exercise-6/
├── Exercise-7/
├── Exercise-8/
├── Exercise-9/
├── Exercise-10/
│
├── Images/
│
└── README.md
```

---

## Learning Objectives

Through these exercises, the following DevOps concepts are explored:

1. Creating and managing Kubernetes Pods and Services.
2. Deploying containerized applications using Minikube.
3. Application scaling and high availability using ReplicaSets.
4. Docker networking and multi-container communication.
5. Container security using AppArmor.
6. Monitoring application metrics using Prometheus and Grafana.
7. Configuring Jenkins for Continuous Integration.
8. Creating and managing Jenkins Freestyle Jobs.
9. Automating application workflows using Jenkins Pipelines.
10. Deploying applications in multi-node Kubernetes clusters.

---

## Screenshots and Demonstrations

The repository includes an `Images` directory containing supporting screenshots and execution demonstrations.

Refer to the individual exercise folders for their respective configuration files, source code, commands, and implementation details.

---

## How to Use This Repository

Clone the repository:

```bash
git clone https://github.com/deva-33-bit/k8s-exercises.git
```

Navigate into the project:

```bash
cd k8s-exercises
```

Open the required exercise folder:

```bash
cd Exercise-1
```

Follow the instructions and commands provided in the respective exercise files.

---

## Author

**Devendra E**

GitHub: [@deva-33-bit](https://github.com/deva-33-bit)

---

*This repository is maintained as part of hands-on DevOps laboratory learning and practical implementation.*
