🚀 Dockerized Static Website with CI/CD Deployment

This project demonstrates how to build and deploy a simple static website using Docker, automated CI/CD with GitHub Actions, and deployment on Amazon EC2.

Whenever code is pushed to the main branch, the pipeline automatically updates the running application on the EC2 server.


🏗 Project Architecture.
Developer Push
      ↓
GitHub Repository
      ↓
GitHub Actions CI/CD
      ↓
SSH Deployment
      ↓
EC2 Server
      ↓
Docker Container Running Website

The application container is pulled from Docker Hub and restarted automatically on deployment.

📂 Project Structure
web-cicd-project/
│
├── index.html
├── style.css
├── script.js
├── Dockerfile
│
├── deploy.sh
│
└── .github/
    └── workflows/
        └── deploy.yml
⚙️ Technologies Used

HTML / CSS / JavaScript

Docker

GitHub Actions

Amazon EC2

Docker Hub

Nginx (for serving static files inside container)

🐳 Docker Image

The website is containerized using a simple Dockerfile.

Build Image
docker build -t simple-website .
Run Container
docker run -d -p 80:80 simple-website
☁️ EC2 Deployment

The application runs inside a Docker container on an Amazon EC2 instance.

SSH into server
ssh ubuntu@13.51.238.105
Pull latest image
docker pull YOUR_DOCKERHUB_USERNAME/simple-website
Run container
docker run -d -p 80:80 --name website YOUR_DOCKERHUB_USERNAME/simple-website
🔁 CI/CD Pipeline

A workflow in GitHub Actions automatically deploys the latest version.

Trigger
Push to main branch
Workflow Steps

1️⃣ Code pushed to GitHub
2️⃣ GitHub Actions starts pipeline
3️⃣ Pipeline connects to EC2 via SSH
4️⃣ Pulls latest Docker image
5️⃣ Stops old container
6️⃣ Starts new container

🔐 GitHub Secrets

The following secrets are required in the repository settings:

Secret Name	Description
EC2_HOST	EC2 public IP
EC2_USER	EC2 username
EC2_SSH_KEY	Private SSH key for server login
🚀 Deployment Script

The server runs a small deployment script:

#!/bin/bash

docker pull YOUR_DOCKERHUB_USERNAME/simple-website

docker stop website || true
docker rm website || true

docker run -d -p 80:80 --name website YOUR_DOCKERHUB_USERNAME/simple-website
📌 Key Features

✅ Dockerized application
✅ Automated CI/CD pipeline
✅ Remote deployment via SSH
✅ Production-style container restart
✅ Cloud deployment on AWS

🎯 Learning Outcomes

This project demonstrates practical DevOps skills including:

Containerization with Docker

CI/CD automation

Cloud deployment

Secure SSH-based automation

Infrastructure automation concepts

👨‍💻 Author

Irfan Ali


