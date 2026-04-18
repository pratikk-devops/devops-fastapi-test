#  DevOps Project FastAPI Application 

------------------------------------------------------------------------

##  Overview

This project demonstrates a complete DevOps workflow for a simple
FastAPI application. The application allows users to store and retrieve
user data using a JSON file instead of a database.

###  Objectives Covered

-   Dockerization
-   Container orchestration using Docker Compose
-   Data persistence using volumes
-   Automated CI/CD using Jenkins (webhook, GitHook trigers)
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

##  Data Storage Mechanism

Data is stored in: app/data/users.json

-   File is automatically created when `/users` endpoint is accessed
-   No database is used

------------------------------------------------------------------------

## 🐳 Docker Setup

### Run Application

``` bash
docker compose up --build
```

------------------------------------------------------------------------

###  Services

  Service      Port
  ------------ ------
  FastAPI      8000
  Prometheus   9090
  Grafana      3000

------------------------------------------------------------------------

##  Data Persistence

Docker volume: app_data:/app/app/data

###  Purpose

Ensures `users.json` persists even after container deletion

------------------------------------------------------------------------

## 🔁 Persistence Verification

1.  Add user via API\
2.  Run:

``` bash
docker compose down
docker compose up -d
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
-   URL: http://`<EC2-IP>`:9090

------------------------------------------------------------------------

###  Grafana

-   URL: http://`<EC2-IP>`:3000
-   Default login: admin / admin

------------------------------------------------------------------------

## ☁️ EC2 Deployment

Steps: 1. Launch Ubuntu EC2 instance\
2. Install Docker & Docker Compose V2\
3. Clone repository\
4. Run docker compose up -d

------------------------------------------------------------------------

###  Required Ports

  Port   Purpose
  ------ ------------
  8000   FastAPI
  9090   Prometheus
  3000   Grafana
  8080   Jenkins

------------------------------------------------------------------------


## 📂 Project Structure

``` bash
project/ 
    ├── app/data/info.txt users.json
    ├── Dockerfile 
    ├── docker-compose.yml
    ├── prometheus.yml 
    ├── Jenkinsfile 
    ├── requirements.txt 
    ├── README.md
```












------------------------------------------------------------------------

##  Testing

Swagger UI: http://`<EC2-IP>`:8000/docs

------------------------------------------------------------------------

##  Conclusion

This project demonstrates: - Containerized deployment - Persistent
storage without database - Automated CI/CD pipeline - Monitoring and
observability

------------------------------------------------------------------------
