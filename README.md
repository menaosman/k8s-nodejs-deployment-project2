# k8s-nodejs-deployment-project2
"Kubernetes project for deploying Node.js with PVC, LoadBalancer, and rolling updates"
# 🚀 Node.js Kubernetes Deployment Project

A complete Kubernetes DevOps lab to deploy a simple Node.js application with persistent storage, external access via LoadBalancer, and zero-downtime rolling updates.

---

## 🌟 Project Overview

This project demonstrates the deployment of a containerized Node.js application in a Kubernetes cluster. It showcases:
- 📦 Deployment of the app using `Deployment` YAML
- 💾 Persistent data storage via `PersistentVolumeClaim`
- 🌐 External access via a `LoadBalancer` service
- 🔁 Rolling updates with zero downtime

---

## 📂 File Structure

```
.
├── node-deployment.yaml             # Node.js app deployment config
├── pvc.yaml                         # PersistentVolumeClaim definition
├── loadbalancer-service.yaml       # LoadBalancer service for external access
├── rolling-update-deployment.yaml  # Updated deployment with rolling strategy
├── screenshots/                    # Command output screenshots
└── README.md
```

---

## 🛠️ Technologies Used

- 🐳 Docker
- ☸️ Kubernetes
- 📁 Persistent Volume & PVC
- 🔁 Rolling Updates
- 📦 Node.js
- 🔧 kubectl CLI

---

## ⚙️ Setup Instructions

### 1️⃣ Prerequisites
- ✅ Minikube or Kubernetes Cluster
- ✅ kubectl CLI
- ✅ Docker installed locally

### 2️⃣ Run the project locally

```bash
# Step 1: Start Minikube
minikube start

# Step 2: Deploy Node.js App
kubectl apply -f node-deployment.yaml

# Step 3: Create and bind persistent volume
kubectl apply -f pvc.yaml

# Step 4: Expose with LoadBalancer
kubectl apply -f loadbalancer-service.yaml

# Step 5: Rolling update (Optional)
kubectl apply -f rolling-update-deployment.yaml

# Step 6: Get the external IP
minikube service nodejs-service --url
```

---

## 🧪 Output Screenshots

| 📸 Screenshot | Description |
|--------------|-------------|
| ![Deployment] | Successful pod deployment |
| ![PVC] | PVC bound to pod |
| ![Service] | LoadBalancer service created |
| ![Rolling Update] | Rolling update in action |

---

## 👥 Team Contributions

| Member         | GitHub Username     | Task                                              | Output |
|----------------|---------------------|---------------------------------------------------|--------|
| **Seif**       | [z31ny](https://github.com/z31ny)                   | Node.js Deployment YAML + Rolling update setup    | `node-deployment.yaml`, `rolling-update.yaml` |
| **Marwan**     | [MarwanTamerMo](https://github.com/MarwanTamerMo)   | PVC creation and binding                          | `pvc.yaml`, volume tests |
| **Sarah**      | [sarahelansaryy](https://github.com/sarahelansaryy) | LoadBalancer YAML + Service connectivity check    | `loadbalancer-service.yaml`, external IP |
| **Mena**    |[menaosman](https://github.com/menaosman)    | Liveness & Readiness Probes + Testing and team coordination   | Deployment probes |
| **Menna**      | [mennaazazyy](https://github.com/mennaazazyy)       | Screenshot documentation & visuals                | `/screenshots` |
| **Basmala**       |  [basmala352004](https://github.com/basmala352004)          | Final README formatting and Writing the Report   | `README.md`, GitHub repo |

📝 _Each member documented their process and submitted screenshots in the `/screenshots` folder._

---

## 🛠️ Known Issues / To Do

- [ ] Add a ConfigMap for environment variables
- [ ] Integrate a Secret for sensitive config (e.g., DB password)
- [ ] Add readiness and liveness probes

---
## 📬 Contact

If you want to collaborate or have suggestions, feel free to reach out!

```
Team GitHub Profiles:
- Mena: https://github.com/menaosman
- Basmala: https://github.com/basmala352004
- Marwan: https://github.com/MarwanTamerMo
- Sarah: https://github.com/sarahelansaryy
- Menna: https://github.com/mennaazazyy
- Seif: https://github.com/z31ny
```

---

## ⭐ Final Notes

This project follows the best practices of modern DevOps pipelines and showcases practical skills in Kubernetes. Perfect for portfolios, job demos, and team-based infrastructure learning.

---
