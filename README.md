
git add README.md

git commit -m https://hub.docker.com/repository/docker/balajithangapandi/brain-tasks-app/general

git push


# Brain Tasks App - DevOps Deployment Project

## Project Overview

This project demonstrates DevOps implementation using:

- Docker
- DockerHub
- AWS CLI
- Kubernetes
- Amazon EKS
- AWS CodeBuild
- AWS CodePipeline
- CloudWatch

Application Repository:
https://github.com/Vennilavanguvi/Brain-Tasks-App.git

---

# Step 1 - Clone Repository

```bash
git clone https://github.com/Vennilavanguvi/Brain-Tasks-App.git
```

---

# Step 2 - Dockerize Application

## Dockerfile

```dockerfile
FROM nginx:alpine

COPY dist/ /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

---

# Build Docker Image

```bash
docker build -t brain-tasks-app .
```

---

# Run Docker Container

```bash
docker run -d -p 3000:80 --name brain-container brain-tasks-app
```

Application URL:

```text
http://localhost:3000
```

---

# Step 3 - DockerHub Repository

DockerHub Link:

https://hub.docker.com/r/balajithangapandi/brain-tasks-app

---

# Push Docker Image

```bash
docker login

docker tag brain-tasks-app balajithangapandi/brain-tasks-app:latest

docker push balajithangapandi/brain-tasks-app:latest
```

---

# Step 4 - AWS CLI Configuration

```bash
aws configure
```

Verify AWS:

```bash
aws sts get-caller-identity
```

---

# Step 5 - Kubernetes Tools

Installed:
- kubectl
- eksctl

Verify kubectl:

```bash
kubectl version --client
```

Verify eksctl:

```bash
eksctl version
```

---

# Step 6 - EKS Cluster Creation

```bash
eksctl create cluster \
--name brain-cluster \
--region ap-south-1 \
--nodegroup-name linux-nodes \
--node-type t3.micro \
--nodes 1
```

---

# Step 7 - Kubernetes YAML Files

## deployment.yaml

Creates Kubernetes deployment for application pods.

## service.yaml

Creates LoadBalancer service for application access.

Apply Commands:

```bash
kubectl apply -f deployment.yaml

kubectl apply -f service.yaml
```

---

# Step 8 - AWS CodeBuild

Created buildspec.yml for automated build process.

---

# Step 9 - AWS CodePipeline

Pipeline Flow:

GitHub → CodeBuild → Docker Build → EKS Deployment

---

# Step 10 - Monitoring

CloudWatch Logs used for:
- Build monitoring
- Deployment monitoring
- Application logs

---





































































































