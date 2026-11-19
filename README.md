# Kubernetes Web Hosting & Reliability Lab

An independent infrastructure engineering project demonstrating Kubernetes deployment, workload reliability, container health monitoring, resource management and observability using Prometheus and Grafana.

## Project Overview

This project builds a local Kubernetes environment to simulate the deployment and monitoring of a web application.

An Nginx application is deployed across two replicas, with Kubernetes managing workload health, recovery and application availability. Prometheus collects infrastructure and workload metrics, while Grafana provides dashboards for monitoring CPU usage, memory consumption and Pod readiness.

The project explores practical Site Reliability Engineering (SRE) concepts through hands-on implementation and testing.

## Architecture

**Environment:** Windows 11, WSL2 (Ubuntu), Docker Desktop and Minikube.

**Technology stack:**
- Kubernetes – workload orchestration
- Minikube – local Kubernetes cluster
- Docker – container runtime
- Nginx – web application
- Helm – Kubernetes package management
- Prometheus – metrics collection
- Grafana – monitoring and visualisation
- Metrics Server – resource utilisation metrics
- YAML – declarative Kubernetes configuration

## Implementation

### 1. Kubernetes Cluster Setup
- Installed and configured Minikube using the Docker driver.
- Created a local Kubernetes cluster.
- Inspected cluster nodes and namespaces using kubectl.

### 2. Application Deployment
- Deployed Nginx using a Kubernetes Deployment with two replicas.
- Exposed the application through a NodePort Service.
- Created a declarative Deployment manifest.

### 3. Workload Reliability
- Configured HTTP readiness and liveness probes.
- Defined container CPU and memory requests and limits.
- Performed rolling updates to change the Nginx image.
- Simulated an unsuccessful image update and investigated the resulting ImagePullBackOff condition.
- Manually rolled back the failed deployment using Kubernetes rollout history and rollback commands.
- Deleted an application Pod and verified that Kubernetes automatically created a replacement.

### 4. Monitoring and Observability
- Enabled Metrics Server to collect node and Pod resource utilisation.
- Installed the kube-prometheus-stack using Helm.
- Configured Prometheus and Grafana in a dedicated monitoring namespace.
- Queried Prometheus metrics to inspect workload health, CPU and memory usage.
- Created a Grafana dashboard displaying:
  - Nginx Pod CPU usage
  - Nginx Pod memory consumption
  - Nginx Pod readiness

### 5. Reliability Testing
- Verified application availability through the Kubernetes Service.
- Observed automatic Pod replacement following deletion.
- Tested rolling updates and manual rollback.
- Investigated historical metric series following Pod replacement.
- Configured a Grafana alert rule for detecting Nginx Pods that are not Ready. External email notification delivery remains unconfigured.

## Key Learning Outcomes

- Kubernetes Deployments, ReplicaSets, Pods and Services
- Declarative infrastructure configuration using YAML
- Container health checks and resource management
- Kubernetes self-healing and rollout strategies
- Troubleshooting failed container image deployments
- Prometheus metrics and PromQL queries
- Grafana dashboards and alert-rule configuration
- Helm-based installation of Kubernetes monitoring components

## Repository Structure

```text
kubernetes-web-hosting-reliability/
│
├── README.md
├── nginx-deployment.yaml
├── monitoring-values.yaml
└── screenshots/
```

## Project Status

Completed core deployment, reliability testing and monitoring implementation. Further development may include alert notification delivery, additional monitoring panels and automated deployment workflows.

## About

This is an independent learning and portfolio project. It demonstrates practical Kubernetes and observability skills in a local lab environment and does not represent production Kubernetes administration experience.
