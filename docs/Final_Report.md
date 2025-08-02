# Kubernetes Node.js Deployment -  Report

## 1. Objectives

This project demonstrates a full DevOps pipeline using Kubernetes to:

- Deploy a Node.js application using a Deployment object with 2 replicas.
- Mount persistent storage using a PersistentVolumeClaim (PVC).
- Expose the application to external users using a LoadBalancer Service.
- Perform a zero-downtime rolling update of the application.

---

## 2. Explanation of Work Done

In this demo, we deployed a Node.js app to Kubernetes using a Deployment with 2 replicas.  
We attached a PersistentVolumeClaim (PVC) to mount a directory inside the container at `/app/data`.  
We verified the mount by creating a test file. Then, we exposed the app externally using a LoadBalancer Service and confirmed it's accessible in the browser.  
Finally, we performed a rolling update by changing the image from Node 18 to Node 20. Kubernetes updated each pod one-by-one without downtime.  
The updated pod confirmed the change with version `v20.19.4`.  
This completes the Kubernetes deployment pipeline.

---

## 3. Pre-Testing Summary and Key Steps

### a. Node.js Application Deployment Preparation

- Configured `node-deployment.yaml` to run 2 replicas of a lightweight Node.js server.
- Set the container to listen on port 3000 and return a simple HTTP response.
- Defined resource limits and mounted the PVC to `/app/data`.
- Faced and resolved issues with port alignment and YAML indentation.

### b. Persistent Volume Claim (PVC) Feature Development

- Cloned the repo and created a new working branch.
- Edited `node-pvc.yaml` to request 1Gi storage and confirmed `Bound` status.
- Updated the deployment to mount the volume and verified file persistence across pods.
- Fixed YAML indentation issues for `volumeMounts` and `volumes`.

### c. LoadBalancer Service Configuration

- Ensured Minikube was running and deployment was applied.
- Created a LoadBalancer service with correct `targetPort` and selector.
- Used `minikube tunnel` to expose the service.
- Verified the IP and accessed the app using browser and `curl`.

### d. Rolling Update Implementation

- Configured the deployment with `maxSurge: 1` and `maxUnavailable: 1`.
- Changed the image from `node:18-alpine` to `node:20-alpine`.
- Applied the update and monitored the rollout.
- Verified that new pods were created successfully.
- Confirmed update with `node -v` returning `v20.19.4`.

---

## 4. Commands Used

```bash
minikube start
kubectl apply -f manifests/node-pvc.yaml
kubectl get pvc
kubectl apply -f manifests/node-deployment.yaml
kubectl get pods
kubectl exec -it <pod-name> -- sh
cd /app/data && touch test.txt && ls
kubectl apply -f manifests/node-service.yaml
minikube service nodejs-service
nano manifests/node-deployment.yaml  # change image to node:20-alpine
kubectl apply -f manifests/node-deployment.yaml
kubectl rollout status deployment/nodejs-app-deployment
kubectl get pods -o wide
kubectl exec -it <new-pod-name> -- node -v
```

---

## 5. Screenshots

Refer to the **testing_screenshots.pdf** for:
- `kubectl get pods` output
- File creation test in `/app/data`
- Browser response
- Rollout progress
- Version check

---

## 6. Summary

This project successfully implemented a production-style Kubernetes workflow, including persistent storage, external access, and zero-downtime application updates.  
Each step was verified using appropriate `kubectl` commands, and the final application responded as expected after the update.  
This setup is foundational to real-world DevOps practices and CI/CD pipelines.
