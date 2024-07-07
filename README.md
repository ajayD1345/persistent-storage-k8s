# persistent-storage-k8s
 MySQL Deployment on Kubernetes with Persistent Volumes (PVs) and Persistent Volume Claims (PVCs)

## Overview

This project demonstrates how to deploy a MySQL database on Kubernetes using Persistent Volumes (PVs) and Persistent Volume Claims (PVCs). The setup ensures that MySQL data persists even if the MySQL Pod restarts or moves to a different node within the Kubernetes cluster.

## Prerequisites

Before you begin, ensure you have the following installed:

- Kubernetes cluster (e.g., Minikube, Docker Desktop Kubernetes, or a cloud-based Kubernetes service)
- kubectl command-line tool configured to communicate with your Kubernetes cluster
- Basic understanding of Kubernetes concepts like Pods, Deployments, Persistent Volumes (PVs), and Persistent Volume Claims (PVCs)

## Project Structure

The project folder contains the following files:

- **mysql-pv.yml**: Defines the Persistent Volume (PV) configuration for MySQL data storage.
- **mysql-pvc.yml**: Specifies the Persistent Volume Claim (PVC) to request storage from a Storage Class.
- **mysql-deployment.yml**: Describes the Deployment for MySQL, including container specifications and volume mounts.

## Deploying MySQL

1. **Apply Persistent Volume (PV)**:
   ```
   kubectl apply -f mysql-pv.yaml

   ```
2. **Apply Persistent Volume Claim (PVC):**
   ```
   kubectl apply -f mysql-pvc.yml

   ```
3. **Deploy MySQL using Deployment:**
   ```
   kubectl apply -f mysql-deployment.yml

   ```
4. **Verify Deployment:**
   ```
   kubectl get pods

   ```
5. **Access MySQL:**

- To access MySQL from within the cluster:
  ```
  kubectl exec -it <mysql-pod-name> -- mysql -u root -p

  ```
- To get your <msql-pod-name>, use 'kubectl get pods' to see all your pods, then locate your msql pod under names to get the name of your pod.
## Customization

- Storage Configuration: Adjust the storage size and access modes in mysql-pv.yml and mysql-pvc.yml as per your requirements.
- MySQL Configuration: Customize MySQL settings such as passwords and environment variables in mysql-deployment.yml.

## Cleanup
- To clean up resources created by this project, run:
  ```
  kubectl delete -f mysql-deployment.yml
  kubectl delete -f mysql-pvc.yml
  kubectl delete -f mysql-pv.yml

  ```
## Authur
Hamed Ayojide
