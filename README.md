🚀 Discover Dollar – DevOps Engineer Intern Assignment
📌 Project Overview

This project demonstrates the containerization, CI/CD automation, and cloud deployment of a full-stack MEAN (MongoDB, Express, Angular, Node.js) application as part of the Discover Dollar DevOps Engineer Intern assignment.

The goal is to:

Containerize frontend and backend services

Deploy them using Docker Compose

Automate build & deployment using CI/CD

Expose the application via Nginx reverse proxy on port 80

Run everything on a cloud-based Ubuntu VM (AWS EC2)

🧱 Tech Stack Used

Frontend: Angular

Backend: Node.js + Express

Database: MongoDB

Containerization: Docker & Docker Compose

CI/CD: GitHub Actions

Cloud: AWS EC2 (Ubuntu 22.04)

Reverse Proxy: Nginx

📐 Architecture Overview
User Browser
     |
     |  (Port 80)
     v
  Nginx (Reverse Proxy)
     |
     |----------------------|
     |                      |
Frontend (Angular)      Backend (Node/Express)
                                |
                              MongoDB

📁 Repository Structure
discoverdollar-devops-assignment/
│
├── backend/
│   ├── Dockerfile
│   ├── server.js
│   ├── package.json
│
├── frontend/
│   ├── Dockerfile
│   ├── angular.json
│
├── nginx/
│   └── default.conf
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── docker-compose.yml
└── README.md

▶️ Running the Application Locally (Without Docker)
Backend
cd backend
npm install
npm start


Backend runs on http://localhost:5000

Frontend
cd frontend
npm install
npm start


Frontend runs on http://localhost:4200

🐳 Docker Setup
Backend Dockerfile (Node.js)

Uses node:18-alpine

Installs dependencies

Exposes port 5000

Frontend Dockerfile (Angular + Nginx)

Multi-stage build:

Stage 1: Builds Angular app

Stage 2: Serves build using Nginx

🧩 Docker Compose Setup

The application is deployed using Docker Compose with the following services:

mongo – MongoDB database

backend – Node.js API service

frontend – Angular UI

nginx – Reverse proxy (exposes port 80)

Run using Docker Compose
docker-compose pull
docker-compose up -d

🌐 Cloud Deployment (AWS EC2)
VM Details

OS: Ubuntu 22.04 LTS

Instance type: t2.micro

Open ports:

22 (SSH)

80 (HTTP)

Setup on EC2
sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker ubuntu


Clone repo and deploy:

git clone https://github.com/<your-username>/discoverdollar-devops-assignment.git

cd discoverdollar-devops-assignment

docker-compose up -d


✅ Application accessible at:

http://<EC2_PUBLIC_IP>

🔄 CI/CD Pipeline (GitHub Actions)
Workflow Overview

On every push to the main branch:

GitHub Actions triggers the pipeline

Builds Docker images (frontend & backend)

Pushes images to Docker Hub

SSHs into EC2 instance

Pulls latest images & restarts containers

Key Secrets Used

DOCKER_USERNAME

DOCKER_PASSWORD

VM_IP

SSH_KEY

🔁 Nginx Reverse Proxy Configuration

Routes / → Frontend (Angular)

Routes /api/ → Backend (Node.js)

Entire application served via port 80

Example:

server {
  listen 80;

  location / {
    proxy_pass http://frontend;
  }

  location /api/ {
    proxy_pass http://backend:5000/;
  }
}

📸 Screenshots (Attached in Repository)

✔ Docker image build & push (Docker Hub)
✔ GitHub Actions CI/CD execution
✔ EC2 instance running
✔ docker ps showing all containers
✔ Application UI running on browser
✔ Nginx configuration
<img width="1656" height="950" alt="Screenshot (212)" src="https://github.com/user-attachments/assets/5c515b8f-1a1c-4019-97d3-1a3edcb0a7ae" />

✅ Final Verification Checklist

 Application loads on EC2 IP using port 80

 Containers restart automatically on new commit

 CI/CD pipeline runs successfully

 MongoDB persists data via volume
<img width="1304" height="971" alt="Screenshot (211)" src="https://github.com/user-attachments/assets/896164a9-2402-4b64-a5ee-2bfd356852d5" />

🛑 Important Note

As requested, the cloud infrastructure has not been deleted and can be restarted for live CI/CD demonstration in future interview rounds.

🙌 Conclusion

This assignment demonstrates real-world DevOps practices including:

Containerization

Infrastructure automation

CI/CD pipelines

Cloud deployment

Reverse proxy configuration
