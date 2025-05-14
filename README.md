# Java Spring Boot Application - CI/CD with Docker, Jenkins & Kubernetes

This project demonstrates a complete CI/CD pipeline using Jenkins to build, containerize, push to Docker Hub, and deploy a Spring Boot application to a Kubernetes cluster.

##  Technologies Used

- Java Spring Boot
- Maven
- Docker
- Jenkins (Pipeline)
- Kubernetes (kubectl)
- GitHub

## Project Structure

- `deployment.yaml` – Kubernetes Deployment file
- `service.yaml` – Kubernetes Service file
- `Dockerfile` – Docker build instructions
- `Jenkinsfile` – CI/CD pipeline configuration

## Jenkins Pipeline Stages

1. **Git Clone** – Clones the application source code from GitHub.
2. **Package** – Builds the project using Maven.
3. **Docker Build** – Creates a Docker image of the application.
4. **Docker Login** – Logs into Docker Hub using stored credentials.
5. **Docker Push** – Pushes the image to Docker Hub.
6. **Docker Run** – Runs a local container (optional).
7. **Deploy to Kubernetes** – Applies deployment and service YAML files to the cluster.

## Docker

Make sure to update the image name in the `Jenkinsfile` and Kubernetes YAML files with your own Docker Hub username.

##  Kubernetes

Ensure your kubeconfig is configured properly and uploaded in Jenkins as a file credential for deployment.

##  Prerequisites

- Jenkins installed and configured
- Docker installed and running
- Kubernetes cluster (local/minikube/EKS)
- Jenkins plugins:
  - Docker Pipeline
  - Kubernetes CLI
  - Credentials Plugin

## Credentials Used

- Docker Hub credentials (`docker-hub`) as username/password
- Kubeconfig file (`kubeconfig`) for kubectl access in Jenkins

---



