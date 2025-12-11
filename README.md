# Final-Project-CST8915
# Best Buy Cloud-Native Microservices Application

### Name- Saizal Saini <br>
### Student Number- 041168394
A fully containerized, Kubernetes-orchestrated microservices system deployed on Azure AKS, with CI/CD pipelines and a production-ready architecture.

**Architecture Diagram**

![alt text](<Screenshot 2025-12-10 201746.png>)


---

## Project Overview

This project implements a cloud-native microservices-based Best Buy Online Store using five independent services and a MongoDB stateful backend.
Each microservice runs in a Docker container and is deployed to Azure Kubernetes Service (AKS) using Kubernetes manifests.

The system follows the Algonquin Pet Store (On Steroids) architecture and includes:

- **Store-Front** – Customer-facing web application (LoadBalancer exposed)
- **Store-Admin** – Admin dashboard web app
- **Product-Service** – Provides product catalog APIs
- **Order-Service** – Handles order creation and retrieval
- **Makeline-Service** – Background worker (order processing)
- **MongoDB StatefulSet** – Persistent backend database

The project also includes GitHub Actions-based CI/CD pipelines.

---

##  Microservices in the System

| Microservice       | Description                                      |
|--------------------|--------------------------------------------------|
| Store-Front        | Public-facing Best Buy UI served through NGINX   |
| Store-Admin        | Admin dashboard for internal operations          |
| Product-Service    | Manages the product catalog and exposes REST APIs|
| Order-Service      | Stores and retrieves customer orders             |
| Makeline-Service   | Background processor that handles order workflow |
| MongoDB            | Stateful database storing product and order data |

---

##  Deployment Instructions

### Build Docker Images

From each microservice folder:

```bash
docker build -t saizalsaini02/<service-name>:v1 .
docker push saizalsaini02/<service-name>:v1
```

Example:

```bash
docker build -t saizalsaini02/product-service:v1 .
docker push saizalsaini02/product-service:v1
```


---

##  CI/CD Pipeline (GitHub Actions)

Each microservice repo contains a `.github/workflows/ci-cd.yaml` pipeline that:

- Builds Docker images
- Pushes them to Docker Hub
- Can trigger Kubernetes deployment (optional)

Example workflow:

```yaml
name: CI/CD

on:
  push:
    branches: ["main"]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - uses: docker/login-action@v3
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker Image
      run: docker build -t saizalsaini02/product-service:latest .

    - name: Push Docker Image
      run: docker push saizalsaini02/product-service:latest
```

---

##  Links Table

| Component         | GitHub Repository | Docker Hub Image                          |
|-------------------|-------------------|-------------------------------------------|
| Store-Front       | https://github.com/sain02/store-front-L9        | https://hub.docker.com/r/saizalsaini02/store-front             |
| Store-Admin       | https://github.com/sain02/store-admin-L9        | https://hub.docker.com/r/saizalsaini02/store-admin           |
| Product-Service   | https://github.com/sain02/product-service-L9       | https://hub.docker.com/r/saizalsaini02/product-service       |
| Order-Service     | https://github.com/sain02/order-service-L9        | https://hub.docker.com/r/saizalsaini02/order-service         |
| Makeline-Service  | https://github.com/sain02/makeline-service-L9       | https://hub.docker.com/r/saizalsaini02/makeline-service       |


---

## 🎥 Demo Video

Insert your YouTube video link here:

 **Demo Video Link**

---

---

##  Conclusion

This project demonstrates:

✔ Cloud-native microservice architecture  
✔ Kubernetes orchestration on Azure  
✔ Docker containerization  
✔ CI/CD automation with GitHub Actions  
✔ Realistic retail-store workflow (Best Buy)  

This completes the required course project with a fully functional, scalable, and production-style system.
