# Mattermost GitOps & CI/CD Project 🚀

![Build Status](http://192.168.49.2:30808/buildStatus/icon?job=Mattermost-GitOps-Pipeline)

A complete GitOps implementation for deploying Mattermost Team Edition on Kubernetes with automated CI/CD checks.

## 🏗️ Architecture
* **Infrastructure**: Kubernetes (Minikube)
* **Application**: Mattermost Team Edition
* **Database**: PostgreSQL with Persistent Storage
* **GitOps**: **ArgoCD** for automated synchronization
* **CI/CD**: **Jenkins** Pipeline for health verification

## 📂 Project Structure
* `k8s/`: Kubernetes manifests (Postgres & Mattermost App).
* `jenkins/`: Jenkinsfile for automated health checks.

## 🚀 Quick Start (Manual Deployment)

1. **Deploy Database**:
   ```bash
   kubectl apply -f k8s/postgres-standalone.yaml
   ```

2. **Setup Database**:
   ```bash
   kubectl exec -it postgres-db -n mattermost -- psql -U mmuser -d postgres -c "ALTER USER mmuser WITH PASSWORD 'password123';"
   kubectl exec -it postgres-db -n mattermost -- psql -U mmuser -d postgres -c "CREATE DATABASE mattermost;"
   ```

3. **Deploy App**:
   ```bash
   kubectl apply -f k8s/mattermost-app.yaml
   ```

## 🔗 Access the Services
* **Mattermost**: `kubectl port-forward svc/mattermost-team-edition 8065:8065 -n mattermost`
* **Jenkins**: `kubectl port-forward svc/jenkins 8080:8080 -n jenkins`

