# 🚀 Mattermost Deployment with GitOps & Jenkins

## 📂 Structure
* **/k8s**: Kubernetes manifests (Postgres & Mattermost App).
* **/jenkins**: Pipeline for automated health checks.

## 🚀 Quick Start
1. **Deploy DB**: `kubectl apply -f k8s/postgres-standalone.yaml`
2. **Setup DB**: 
   - `kubectl exec -it postgres-db -n mattermost -- psql -U mmuser -d postgres -c "ALTER USER mmuser WITH PASSWORD 'password123';"`
   - `kubectl exec -it postgres-db -n mattermost -- psql -U mmuser -d postgres -c "CREATE DATABASE mattermost;"`
3. **Deploy App**: `kubectl apply -f k8s/mattermost-app.yaml`

## 🔗 Port Forwarding
- Mattermost: `kubectl port-forward svc/mattermost-team-edition 8065:8065 -n mattermost`
- Jenkins: `kubectl port-forward svc/jenkins 8080:8080 -n jenkins`
