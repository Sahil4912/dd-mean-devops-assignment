<div align="center">

# 🚀 MEAN Stack CRUD Application with DevOps Pipeline

[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/features/actions)
[![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white)](https://angular.io/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)

**A Containerized MEAN stack application with automated CI/CD deployment demonstrating modern DevOps practices including containerization, CI/CD automation, and cloud deployment.**

[Features](#-features) •
[Architecture](#-architecture) •
[Quick Start](#-quick-start) •
[Deployment](#-deployment) •
[Documentation](#-documentation)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Quick Start](#-quick-start)
- [Project Structure](#-project-structure)
- [Configuration](#-configuration)
- [Deployment](#-deployment)
- [CI/CD Pipeline](#-cicd-pipeline)
- [API Endpoints](#-api-endpoints)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

This project is a comprehensive demonstration of a **Containerized MEAN stack application with automated CI/CD deployment.** (MongoDB, Express.js, Angular, Node.js) with complete DevOps implementation. It showcases industry best practices for containerization, continuous integration/continuous deployment (CI/CD), cloud infrastructure, and reverse proxy configuration.

The application provides a simple yet powerful CRUD (Create, Read, Update, Delete) interface for managing tutorials, built with a multi-container Dockerized architecture and automated deployment pipeline.

---

## ✨ Features

### Application Features
- 📝 **CRUD Operations** - Create, read, update, and delete tutorials
- 🔍 **Search Functionality** - Find tutorials by title
- ✅ **Status Management** - Mark tutorials as published/unpublished
- 🎨 **Responsive UI** - Modern Angular frontend with Bootstrap styling
- 🔄 **Real-time Updates** - Seamless data synchronization

### DevOps Features
- 🐳 **Fully Containerized** - All services run in Docker containers
- 🚀 **Automated CI/CD** - GitHub Actions pipeline for continuous deployment
- ☁️ **Cloud Deployed** - Running on AWS EC2 infrastructure
- 🔄 **Automated Deployment** - Push to main branch triggers automatic redeployment
- 📦 **Container Registry** - Images stored in Docker Hub
- 🔒 Nginx reverse proxy configured for single-port access
- 📊 **Persistent Storage** - MongoDB data persistence with Docker volumes

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        GitHub Repository                         │
│                     (Source Code Version Control)                │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ Push to main branch
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                      GitHub Actions CI/CD                        │
│  ┌──────────────┐  ┌──────────────┐  ┌─────────────────────┐  │
│  │ Build Backend│  │Build Frontend│  │  Push to Docker Hub │  │
│  └──────────────┘  └──────────────┘  └─────────────────────┘  │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ Deploy to Cloud
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                         Docker Hub                               │
│        sahil4912/mean-backend    sahil4912/mean-frontend        │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ Pull Latest Images
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                     AWS EC2 (Ubuntu 24.04)                       │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │              Docker Compose Environment                   │  │
│  │                                                            │  │
│  │  ┌────────────┐  ┌────────────┐  ┌──────────────────┐  │  │
│  │  │  MongoDB   │  │  Backend   │  │  Nginx (Frontend)│  │  │
│  │  │  Container │◄─┤  Container │◄─┤    Container     │  │  │
│  │  │   :27017   │  │   :8080    │  │      :80         │  │  │
│  │  └────────────┘  └────────────┘  └──────────────────┘  │  │
│  │         │                                    │            │  │
│  │         ▼                                    │            │  │
│  │  ┌────────────┐                             │            │  │
│  │  │Persistent  │                             │            │  │
│  │  │  Volume    │                             │            │  │
│  │  │(mongo-data)│                             │            │  │
│  │  └────────────┘                             │            │  │
│  └────────────────────────────────────────────┼────────────┘  │
│                                                 │               │
│                                        Elastic IP               │
└─────────────────────────────────────────────┼─────────────────┘
                                              │
                                              │ http://elastic-ip
                                              ▼
                                    ┌─────────────────┐
                                    │   End Users     │
                                    │  (Web Browsers) │
                                    └─────────────────┘
```

## 🛠️ Tech Stack

### Frontend
- **Angular 15** - Modern TypeScript-based framework
- **Bootstrap** - Responsive UI components
- **RxJS** - Reactive programming for async operations
- **TypeScript** - Type-safe JavaScript

### Backend
- **Node.js 18** - JavaScript runtime environment
- **Express.js 4** - Minimal web framework
- **Mongoose 6** - MongoDB ODM (Object Data Modeling)
- **CORS** - Cross-Origin Resource Sharing middleware

### Database
- **MongoDB 6** - NoSQL document database

### DevOps & Infrastructure
- **Docker** - Container platform
- **Docker Compose** - Multi-container orchestration
- **GitHub Actions** - CI/CD automation
- **Docker Hub** - Container image registry
- **AWS EC2** - Cloud virtual machine (Ubuntu 24.04 LTS)
- **Nginx** - Web server and reverse proxy

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Docker** (version 20.10 or higher)
- **Docker Compose** (version 2.0 or higher)
- **Git** (for cloning the repository)
- **AWS Account** (for cloud deployment)
- **Docker Hub Account** (for image registry)
- **GitHub Account** (for CI/CD)

### Installation Guides

<details>
<summary><b>🐧 Installing on Ubuntu/Debian</b></summary>

```bash
# Update package index
sudo apt update

# Install Docker
sudo apt install -y docker.io

# Install Docker Compose
sudo apt install -y docker-compose

# Add your user to docker group (optional, to run without sudo)
sudo usermod -aG docker $USER
newgrp docker
```
</details>

<details>
<summary><b>🍎 Installing on macOS</b></summary>

```bash
# Using Homebrew
brew install docker
brew install docker-compose

# Or download Docker Desktop for Mac
# https://www.docker.com/products/docker-desktop
```
</details>


---

## 🚀 Quick Start

### Local Development Setup

1. **Clone the Repository**
   ```bash
   git clone <your-repository-url>
   cd dd-mean-devops-assignment
   ```

2. **Start the Application**
   ```bash
   docker-compose up -d --build
   ```

3. **Verify Containers are Running**
   ```bash
   docker ps
   ```
   
   You should see three containers:
   - `mongodb` - Database
   - `backend` - API Server
   - `nginx` - Frontend & Reverse Proxy

4. **Access the Application**
   
   Open your browser and navigate to:
   ```
   http://localhost
   ```

5. **Stop the Application**
   ```bash
   docker-compose down
   ```

6. **View Logs**
   ```bash
   # All containers
   docker-compose logs -f
   
   # Specific container
   docker-compose logs -f backend
   docker-compose logs -f nginx
   docker-compose logs -f mongodb
   ```

---

## 📁 Project Structure

```
crud-dd-task-mean-app/
├── .github/
│   └── workflows/
│       └── ci-cd.yml           # GitHub Actions CI/CD pipeline
├── backend/
│   ├── app/
│   │   ├── config/
│   │   │   └── db.config.js    # Database configuration
│   │   ├── controllers/
│   │   │   └── tutorial.controller.js  # Business logic
│   │   ├── models/
│   │   │   ├── index.js        # Mongoose setup
│   │   │   └── tutorial.model.js       # Tutorial schema
│   │   └── routes/
│   │       └── turorial.routes.js      # API routes
│   ├── Dockerfile              # Backend container definition
│   ├── package.json            # Backend dependencies
│   └── server.js               # Express server entry point
├── frontend/
│   ├── src/
│   │   ├── app/
│   │   │   ├── components/
│   │   │   │   ├── add-tutorial/
│   │   │   │   ├── tutorial-details/
│   │   │   │   └── tutorials-list/
│   │   │   ├── models/
│   │   │   │   └── tutorial.model.ts
│   │   │   ├── services/
│   │   │   │   └── tutorial.service.ts
│   │   │   ├── app-routing.module.ts
│   │   │   ├── app.component.*
│   │   │   └── app.module.ts
│   │   ├── assets/
│   │   ├── index.html
│   │   ├── main.ts
│   │   └── styles.css
│   ├── angular.json            # Angular configuration
│   ├── Dockerfile              # Frontend multi-stage build
│   ├── package.json            # Frontend dependencies
│   └── tsconfig.json           # TypeScript configuration
├── nginx/
│   └── nginx.conf              # Nginx reverse proxy config
├── docker-compose.yml          # Multi-container orchestration
├── README.md                   # This file
└── screenshots/                # Application screenshots
```

---

## ⚙️ Configuration

### Environment Variables

The application uses the following default configurations:

**Backend (`backend/app/config/db.config.js`)**
```javascript
module.exports = {
  url: "mongodb://mongodb:27017/tutorials_db"
};
```

**Frontend (`frontend/src/app/services/tutorial.service.ts`)**
```typescript
baseURL = 'http://localhost/api';
```

### Docker Compose Configuration

**Key Services:**

```yaml
services:
  mongodb:
    image: mongo:6
    volumes:
      - mongo-data:/data/db
    
  backend:
    build: ./backend
    depends_on:
      - mongodb
    
  nginx:
    build: ./frontend
    ports:
      - "80:80"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - backend
```

### Nginx Reverse Proxy

```nginx
location / {
    # Serve Angular static files
    try_files $uri $uri/ /index.html;
}

location /api/ {
    # Proxy API requests to backend
    proxy_pass http://backend:8080;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
}
```

---

## ☁️ Deployment

### AWS EC2 Deployment Guide

#### Step 1: Launch EC2 Instance

1. **Log in to AWS Console**
   - Navigate to EC2 Dashboard
   
2. **Launch Instance**
   - **AMI**: Ubuntu Server 24.04 LTS
   - **Instance Type**: t3.small (or larger)
   - **Storage**: 20 GB or more
   - **Security Group**:
     - Port 22 (SSH) - Your IP
     - Port 80 (HTTP) - 0.0.0.0/0

3. **Allocate Elastic IP**
   - Associate with your EC2 instance
   - Note down the Elastic IP address

#### Step 2: Connect to EC2 Instance

```bash
# SSH into your instance
ssh -i your-key.pem ubuntu@<your-elastic-ip>
```

#### Step 3: Install Docker & Docker Compose

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Docker
sudo apt install -y docker.io

# Install Docker Compose
sudo apt install -y docker-compose

# Add user to docker group
sudo usermod -aG docker ubuntu
newgrp docker

# Verify installation
docker --version
docker-compose --version
```

#### Step 4: Deploy Application

```bash
# Clone your repository
git clone <your-repository-url>
cd crud-dd-task-mean-app

# Start the application
sudo docker-compose up -d --build

# Verify containers are running
docker ps

# Check logs
docker-compose logs -f
```

#### Step 5: Access Your Application

Open your browser and navigate to:
```
http://<your-elastic-ip>
```

### Manual Deployment (Without CI/CD)

If you want to deploy without CI/CD:

```bash
# On your EC2 instance
cd ~/crud-dd-task-mean-app

# Pull latest code
git pull origin main

# Rebuild and restart containers
sudo docker-compose down
sudo docker-compose up -d --build
```

---

## 🔄 CI/CD Pipeline

### GitHub Actions Workflow

The CI/CD pipeline is triggered automatically when code is pushed to the `main` branch.

#### Workflow Configuration

The workflow file (`.github/workflows/ci-cd.yml`) performs:

1. ✅ **Code Checkout** - Gets latest code from repository
2. ✅ **Docker Login** - Authenticates with Docker Hub
3. ✅ **Build Images** - Creates backend and frontend Docker images
4. ✅ **Push Images** - Uploads images to Docker Hub registry
5. ✅ **Deploy** - SSH to EC2, pulls images, and restarts containers

### Required GitHub Secrets

Configure these secrets in your GitHub repository:

| Secret Name | Description | Example |
|------------|-------------|---------|
| `DOCKERHUB_USERNAME` | Your Docker Hub username | `sahil4912` |
| `DOCKERHUB_TOKEN` | Docker Hub access token | `dckr_pat_...` |
| `EC2_HOST` | EC2 instance Elastic IP | `54.123.45.67` |
| `EC2_USER` | EC2 SSH username | `ubuntu` |
| `EC2_SSH_KEY` | Private SSH key for EC2 | `-----BEGIN RSA PRIVATE KEY-----...` |

### Setting Up GitHub Secrets

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Add each secret with its corresponding value

### Docker Hub Images

The pipeline pushes images to:
- `sahil4912/mean-backend:latest`
- `sahil4912/mean-frontend:latest`

---

## 🔌 API Endpoints

### Base URL
```
http://<Elastic-IP>/api
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/tutorials` | Retrieve all tutorials |
| `GET` | `/api/tutorials/:id` | Get a specific tutorial by ID |
| `GET` | `/api/tutorials/published` | Get all published tutorials |
| `GET` | `/api/tutorials?title=[keyword]` | Search tutorials by title |
| `POST` | `/api/tutorials` | Create a new tutorial |
| `PUT` | `/api/tutorials/:id` | Update a tutorial by ID |
| `DELETE` | `/api/tutorials/:id` | Delete a tutorial by ID |
| `DELETE` | `/api/tutorials` | Delete all tutorials |

### Request/Response Examples

<details>
<summary><b>Create Tutorial</b></summary>

**Request:**
```http
POST /api/tutorials
Content-Type: application/json

{
  "title": "Docker Tutorial",
  "description": "Learn Docker containerization",
  "published": false
}
```

**Response:**
```json
{
  "_id": "64a1b2c3d4e5f6g7h8i9j0",
  "title": "Docker Tutorial",
  "description": "Learn Docker containerization",
  "published": false,
  "createdAt": "2024-02-24T10:30:00.000Z",
  "updatedAt": "2024-02-24T10:30:00.000Z"
}
```
</details>

<details>
<summary><b>Get All Tutorials</b></summary>

**Request:**
```http
GET /api/tutorials
```

**Response:**
```json
[
  {
    "_id": "64a1b2c3d4e5f6g7h8i9j0",
    "title": "Docker Tutorial",
    "description": "Learn Docker containerization",
    "published": true,
    "createdAt": "2024-02-24T10:30:00.000Z",
    "updatedAt": "2024-02-24T10:30:00.000Z"
  },
  {
    "_id": "64a1b2c3d4e5f6g7h8i9j1",
    "title": "Kubernetes Guide",
    "description": "Master Kubernetes orchestration",
    "published": false,
    "createdAt": "2024-02-24T11:15:00.000Z",
    "updatedAt": "2024-02-24T11:15:00.000Z"
  }
]
```
</details>

<details>
<summary><b>Update Tutorial</b></summary>

**Request:**
```http
PUT /api/tutorials/64a1b2c3d4e5f6g7h8i9j0
Content-Type: application/json

{
  "title": "Docker Tutorial - Updated",
  "description": "Complete Docker guide",
  "published": true
}
```

**Response:**
```json
{
  "message": "Tutorial was updated successfully."
}
```
</details>

---

## 🐛 Troubleshooting

### Common Issues and Solutions

#### Issue: Containers won't start

**Symptoms:**
```bash
docker ps
# Shows no containers or containers constantly restarting
```

**Solutions:**
```bash
# Check container logs
docker-compose logs

# Check specific service
docker-compose logs backend
docker-compose logs mongodb

# Restart from scratch
docker-compose down -v
docker-compose up -d --build
```

#### Issue: Cannot connect to MongoDB

**Error:**
```
MongooseServerSelectionError: connect ECONNREFUSED 127.0.0.1:27017
```

**Solutions:**
1. Ensure MongoDB container is running:
   ```bash
   docker ps | grep mongodb
   ```

2. Check MongoDB logs:
   ```bash
   docker logs mongodb
   ```

3. Verify database URL in `backend/app/config/db.config.js`:
   ```javascript
   url: "mongodb://mongodb:27017/tutorials_db"
   ```

#### Issue: Frontend not loading

**Symptoms:**
- Blank page or nginx 404 error

**Solutions:**
```bash
# Check nginx logs
docker logs nginx

# Verify nginx configuration
docker exec nginx cat /etc/nginx/nginx.conf

# Rebuild frontend
cd frontend
docker build -t mean-frontend .
```

#### Issue: API requests failing (CORS errors)

**Error:**
```
Access to XMLHttpRequest has been blocked by CORS policy
```

**Solutions:**
1. Verify CORS is enabled in `backend/server.js`
2. Check API base URL in frontend service
3. Ensure nginx proxy configuration is correct

#### Issue: Port 80 already in use

**Error:**
```
Error starting userland proxy: listen tcp4 0.0.0.0:80: bind: address already in use
```

**Solutions:**
```bash
# Check what's using port 80
sudo lsof -i :80

# Stop the conflicting service
sudo systemctl stop apache2  # or nginx, or whatever is running

# Or change the port in docker-compose.yml
ports:
  - "8080:80"  # Use port 8080 instead
```

#### Issue: CI/CD pipeline failing

**Common causes:**
1. **Invalid GitHub Secrets**
   - Verify all secrets are correctly set
   - Regenerate Docker Hub token if expired

2. **SSH Connection Issues**
   - Ensure EC2 security group allows inbound SSH from GitHub Actions IPs
   - Verify SSH key format (should include header/footer)

3. **Docker Hub Rate Limits**
   - Authenticate with Docker Hub before pulling
   - Consider using Docker Hub Pro account

---

## 🙏 Acknowledgments

- **Discover Dollar Inc** - For the internship opportunity and project requirements
- **bezkoder** - Original MEAN stack tutorial application
- **Docker Community** - For excellent containerization tools
- **AWS** - For reliable cloud infrastructure
- **Angular Team** - For the powerful frontend framework
- **MongoDB Team** - For the flexible NoSQL database

---

## 📊 Project Status

This project was developed as part of the **DevOps Engineer Internship Assignment** for **Discover Dollar Inc**.

**Assignment Submission Date:** February 24, 2026

**Status:** ✅ Assignment Completed Successfully

---

## 📸 Screenshots

Screenshots demonstrating the complete deployment can be found in the `/screenshots` directory:

- GitHub Actions CI/CD successful execution
- Docker Hub image repositories
- EC2 instance configuration
- Security group settings
- Running containers (`docker ps` output)
- Application UI and functionality
- Nginx configuration

---

<div align="center">

### ⭐ Star this repository if you found it helpful!

**Built with ❤️ by [Sahil Pawar](https://github.com/sahil4912)**

**DevOps Engineer Internship Assignment - Discover Dollar Inc**

</div>
