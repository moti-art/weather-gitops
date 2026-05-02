# 🎡 Weather App - GitOps Repository

This repository serves as the **Single Source of Truth** for the deployment state of the Weather Application. It follows the GitOps methodology to ensure the cluster state matches the configuration defined here.

## 🏗️ Structure
* **`charts/weather-app`**: The master Helm Chart defining the Backend, Frontend, and Tracker.
* **`values-dev.yaml`**: Environment-specific overrides for the Development namespace (Automated updates).
* **`values-prod.yaml`**: Stable configurations for the Production environment.

## ⚙️ How it Works
1. **Source of Truth:** All Kubernetes manifests are abstracted into Helm templates.
2. **Automation:** When a microservice (Backend/Frontend/Tracker) completes its CI, it updates this repository.
3. **Continuous Delivery:** **ArgoCD** monitors this repo and automatically applies changes to the AWS EKS/K3s cluster.

## 🛠️ Deployment Steps
To manually sync the application (if needed):
```bash
helm upgrade --install weather-app ./charts/weather-app -f ./charts/weather-app/values-dev.yaml -n dev

Maintained by Moti Levi