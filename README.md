# 🚀 MEAN Stack DevOps Deployment Assignment

## 📌 Project Overview

This project demonstrates full containerization, cloud deployment, reverse proxy configuration, and CI/CD automation of a MEAN (MongoDB, Express, Angular, Node.js) CRUD application.

The application is:

* Dockerized (Frontend + Backend + MongoDB)
* Deployed on AWS EC2 (Ubuntu)
* Configured with Nginx reverse proxy
* Automated using GitHub Actions CI/CD
* Integrated with Docker Hub for image registry

---

# 🏗️ Architecture Overview

GitHub (Source Code)
↓
GitHub Actions (CI/CD Pipeline)
↓
Docker Hub (Image Registry)
↓
AWS EC2 (Ubuntu VM)
↓
Docker Compose (MongoDB + Backend + Nginx)
↓
Nginx Reverse Proxy (Port 80)
↓
Accessible via Elastic IP

---

# 🧱 Tech Stack

* **Frontend:** Angular
* **Backend:** Node.js + Express
* **Database:** MongoDB (Docker container)
* **Reverse Proxy:** Nginx
* **Containerization:** Docker & Docker Compose
* **CI/CD:** GitHub Actions
* **Cloud Platform:** AWS EC2 (Ubuntu 24.04 LTS)

---

# 📂 Repository Structure

The repository includes:

* Backend Dockerfile
* Frontend Dockerfile
* docker-compose.yml
* nginx.conf
* .github/workflows/ci-cd.yml
* README.md
* screenshots/ folder

---

# 🐳 Dockerization

## Backend

* Base Image: `node:18`
* Exposes port `8080`
* Runs `server.js`
* Image pushed to Docker Hub:

  * `sahil4912/mean-backend:latest`

## Frontend

* Multi-stage Docker build
* Angular production build
* Final image based on `nginx:alpine`
* Served on port `80`
* Image pushed to Docker Hub:

  * `sahil4912/mean-frontend:latest`

---

# 🗄️ Database Setup

MongoDB is deployed using the official Docker image:

* Image: `mongo:6`
* Persistent volume: `mongo-data`
* Managed via Docker Compose

MongoDB runs internally within the Docker network and is not exposed publicly.

---

# 🔁 Docker Compose Configuration

Services defined:

* mongodb
* backend
* frontend (Nginx reverse proxy)

Key configurations:

* `restart: always`
* Service dependencies using `depends_on`
* Volume for MongoDB persistence
* Port mapping `80:80`

---

# 🌐 Nginx Reverse Proxy

Nginx is configured to:

* Serve Angular frontend
* Proxy `/api` requests to backend container

Example configuration:

```
location /api/ {
    proxy_pass http://backend:8080/api/;
}
```

The complete application is accessible via:

```
http://<Elastic-IP>
```

Only port 80 is exposed as required.

---

# ☁️ AWS Infrastructure

* Cloud Provider: AWS
* Instance Type: t3.small
* OS: Ubuntu 24.04 LTS
* Elastic IP attached
* Security Group:

  * Port 22 (SSH)
  * Port 80 (HTTP)

---

# ⚙️ CI/CD Pipeline (GitHub Actions)

The CI/CD workflow is triggered on push to the `main` branch.

## Pipeline Steps

1. Checkout repository
2. Login to Docker Hub
3. Build backend Docker image
4. Push backend image to Docker Hub
5. Build frontend Docker image
6. Push frontend image to Docker Hub
7. SSH into EC2
8. Pull latest images
9. Restart containers using Docker Compose

Deployment commands executed on EC2:

```
cd ~/dd-mean-devops-assignment
sudo docker-compose pull
sudo docker-compose down
sudo docker-compose up -d
```

This ensures automatic deployment whenever code is pushed to the main branch.

---

# 🔐 GitHub Secrets Used

* DOCKERHUB_USERNAME
* DOCKERHUB_TOKEN
* EC2_HOST
* EC2_USER
* EC2_SSH_KEY

---

# 🚀 Step-by-Step Setup & Deployment Instructions

## 1️⃣ Clone Repository

```
git clone <repository-url>
cd dd-mean-devops-assignment
```

## 2️⃣ Install Docker & Docker Compose (on Ubuntu EC2)

```
sudo apt update
sudo apt install docker.io docker-compose -y
```

## 3️⃣ Run Application

```
sudo docker-compose up -d --build
```

## 4️⃣ Access Application

Open in browser:

```
http://<Elastic-IP>
```

---

# 📸 Screenshots Included

The `/screenshots` folder contains:

* GitHub repository structure
* GitHub Actions CI/CD successful execution
* Docker Hub image repositories
* Docker image build & push confirmation
* EC2 instance details
* Security group configuration
* Running containers (`docker ps`)
* Application working UI
* Nginx configuration file

These screenshots demonstrate:

* CI/CD configuration and execution
* Docker image build and push process
* Application deployment and working UI
* Nginx setup and infrastructure details

---

# ✅ Deliverables Completed

✔ All Dockerfiles included
✔ Docker Compose file included
✔ Complete CI/CD configuration included
✔ Step-by-step setup instructions included
✔ Screenshots provided
✔ Application accessible via port 80
✔ Automated redeployment enabled

---

# 🎯 Final Outcome

* Fully containerized MEAN stack application
* Automated CI/CD pipeline
* Cloud-hosted deployment on AWS
* Nginx reverse proxy configuration
* Production-ready DevOps workflow

---

# 👨‍💻 Author

Sahil Pawar
DevOps Engineer Internship Assignment Submission
