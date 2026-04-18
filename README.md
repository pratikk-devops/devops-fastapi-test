# 🚀 DevOps Project FastAPI Application

------------------------------------------------------------------------

## 📌 Overview

This project demonstrates a complete DevOps workflow for a simple
FastAPI application. The application allows users to store and retrieve
user data using a JSON file instead of a database.

### 🎯 Objectives Covered

-   Dockerization
-   Container orchestration using Docker Compose
-   Data persistence using volumes
-   CI/CD using Jenkins
-   Monitoring using Prometheus & Grafana

------------------------------------------------------------------------

## ⚙️ Application Details

### 📍 API Endpoints

  Method   Endpoint   Description
  -------- ---------- -----------------------
  GET      `/`        Returns hello message
  GET      `/users`   Fetch all users
  POST     `/users`   Add new user

------------------------------------------------------------------------

## 🧠 Data Storage Mechanism

Data is stored in: app/data/users.json

-   File is automatically created when `/users` endpoint is accessed
-   No database is used

------------------------------------------------------------------------

## 🐳 Docker Setup

### ▶️ Run Application

``` bash
docker-compose up --build
```

------------------------------------------------------------------------

### 🔑 Services

  Service      Port
  ------------ ------
  FastAPI      8000
  Prometheus   9090
  Grafana      3000

------------------------------------------------------------------------

## 💾 Data Persistence (Critical Requirement)

Docker volume: app_data:/app/app/data

### ✅ Purpose

Ensures `users.json` persists even after container deletion

------------------------------------------------------------------------

## 🔁 Persistence Verification

1.  Add user via API\
2.  Run:

``` bash
docker-compose down
docker-compose up -d
```

3.  Verify: GET /users

Data remains intact

------------------------------------------------------------------------

## 🔧 Jenkins Pipeline

Stages: - Clone Repository\
- Build Docker Image\
- Restart Containers\
- Verify API

------------------------------------------------------------------------

## 📊 Monitoring Setup

### 🔹 Prometheus

-   Scrapes metrics from `/metrics`
-   URL: http://`<EC2-IP>`{=html}:9090

------------------------------------------------------------------------

### 🔹 Grafana

-   URL: http://`<EC2-IP>`{=html}:3000
-   Default login: admin / admin

------------------------------------------------------------------------

## ☁️ EC2 Deployment

Steps: 1. Launch Ubuntu EC2 instance\
2. Install Docker & Docker Compose\
3. Clone repository\
4. Run docker-compose up -d

------------------------------------------------------------------------

### 🔓 Required Ports

  Port   Purpose
  ------ ------------
  8000   FastAPI
  9090   Prometheus
  3000   Grafana
  8080   Jenkins

------------------------------------------------------------------------

## 📂 Project Structure

project/ ├── app/ ├── Dockerfile ├── docker-compose.yml ├──
prometheus.yml ├── Jenkinsfile ├── requirements.txt ├── README.md

------------------------------------------------------------------------

## 🧪 Testing

Swagger UI: http://`<EC2-IP>`{=html}:8000/docs

------------------------------------------------------------------------

## ⚠️ Important Notes

-   Data file is created dynamically
-   Correct volume path: /app/app/data
-   Prometheus target: fastapi-app:8000

------------------------------------------------------------------------

# 📸 Screenshots (Proof of Work)

1.  FastAPI running (/docs)
2.  POST /users success
3.  users.json file
4.  Data persistence after restart
5.  docker ps output
6.  Jenkins success
7.  Prometheus targets UP
8.  Grafana dashboard
9.  /metrics endpoint

------------------------------------------------------------------------

## 🎯 Conclusion

This project demonstrates: - Containerized deployment - Persistent
storage without database - Automated CI/CD pipeline - Monitoring and
observability

------------------------------------------------------------------------

## ✅ Final Checklist

-   Application runs successfully\
-   Data persists after restart\
-   Jenkins pipeline works\
-   Prometheus collects metrics\
-   Grafana visualizes metrics

------------------------------------------------------------------------
