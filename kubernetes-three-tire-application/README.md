Kubernetes Three-Tier Application Deployment on AWS Using KOPS

📌 Project Overview

This project demonstrates the deployment of a three-tier web application on an AWS-hosted Kubernetes cluster provisioned using KOPS.

The architecture consists of a React frontend, Node.js backend, and MySQL database. Kubernetes manages application deployment, scaling, service discovery, ingress routing, configuration and persistent storage.

🏗️ Architecture

Application Workflow

1. User accesses the application through a web browser.
2. AWS Route 53 optionally resolves the application domain.
3. AWS Load Balancer receives incoming HTTP/HTTPS traffic.
4. NGINX Ingress Controller manages incoming requests.
5. Requests to "/" are routed to the React frontend.
6. Requests to "/api" are routed to the Node.js backend.
7. Backend processes requests and communicates with MySQL.
8. MySQL stores application data using persistent EBS storage.
9. Backend returns the response to the frontend.
10. Frontend displays the response to the user.

Architecture Diagram

Add your architecture image to this repository as "architecture.png".

"Kubernetes Three-Tier Architecture" (architecture.png)

🛠️ Technologies Used

Category| Technologies
Cloud Platform| AWS
Cluster Management| KOPS
Container Orchestration| Kubernetes
Ingress Controller| NGINX
Frontend| React.js, NGINX
Backend| Node.js, Express.js
Database| MySQL
Storage| AWS EBS, PVC
Configuration| ConfigMap
Secrets| Kubernetes Secrets
Networking| ClusterIP, Ingress, Headless Service
Infrastructure| AWS Load Balancer, Security Groups, Route 53
Deployment| Kubernetes YAML

📂 Kubernetes Components

1. Frontend Deployment

- React application served using NGINX.
- Configured with two replicas.
- Exposed internally using ClusterIP Service.

2. Backend Deployment

- Node.js and Express application.
- Configured with two replicas.
- Connects to MySQL through Kubernetes service DNS.

3. MySQL Database

- Deployed using Kubernetes StatefulSet.
- Headless Service provides stable network identity.
- PersistentVolumeClaim manages database storage.
- AWS EBS provides persistent storage.

4. NGINX Ingress Controller

- Routes external traffic based on URL paths.
- "/" routes to the frontend service.
- "/api" routes to the backend service.

5. ConfigMap and Secret

- ConfigMap stores application configuration.
- Kubernetes Secret stores sensitive database credentials.
- Environment variables pass configuration to containers.

🚀 Deployment Workflow

1. Provision Kubernetes cluster using KOPS on AWS.
2. Configure kubectl access to the cluster.
3. Create the production namespace.
4. Deploy NGINX Ingress Controller.
5. Configure ConfigMap and Kubernetes Secret.
6. Deploy MySQL StatefulSet and Headless Service.
7. Configure PersistentVolumeClaim and EBS storage.
8. Deploy Node.js backend application.
9. Deploy React frontend application.
10. Configure Services and Ingress rules.
11. Verify application connectivity and Kubernetes resources.
12. Access the application through the Load Balancer endpoint.

💻 Important Kubernetes Commands

Cluster Management

kubectl get nodes
kubectl get namespaces
kubectl create namespace production
kubectl get pods -n production

Deploy Applications

kubectl apply -f configmap.yaml
kubectl apply -f secret.yaml
kubectl apply -f mysql.yaml
kubectl apply -f backend.yaml
kubectl apply -f frontend.yaml
kubectl apply -f ingress.yaml

Verify Resources

kubectl get pods -n production
kubectl get deployments -n production
kubectl get services -n production
kubectl get ingress -n production
kubectl get pvc -n production

Troubleshooting

kubectl describe pods -n production
kubectl logs deployment/backend -n production
kubectl get events -n production

Access Application

kubectl get svc -n ingress-nginx

Use the external Load Balancer address to access the application.

📚 Key Learning Outcomes

- Kubernetes cluster provisioning and management using KOPS.
- Deploying and managing multi-tier applications.
- Configuring NGINX Ingress Controller.
- Managing frontend and backend replicas.
- Deploying MySQL using StatefulSets.
- Configuring persistent storage using AWS EBS.
- Managing application configurations using ConfigMaps.
- Understanding Kubernetes Secrets.
- Troubleshooting Pods, Services and Ingress resources.
- Understanding cloud-native application architecture.

🔐 Security Best Practices

- Never commit AWS access keys or passwords to GitHub.
- Do not expose database credentials in public YAML files.
- Use Kubernetes Secrets for sensitive configuration.
- Base64 encoding is not encryption.
- Follow least-privilege IAM permissions.

📸 Project Screenshots

Add deployment screenshots inside the "screenshots/" directory as implementation evidence.

📌 Project Status

Architecture and deployment workflow documented. Add the actual Kubernetes manifests, configuration files, deployment screenshots and testing results as the implementation progresses.

---

Author: Yalla Harivamshi

Domain: AWS Cloud & DevOps

Repository: DevOps-Projects
