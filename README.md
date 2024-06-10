# Cloud Native Monitoring Application

## Prerequisites

Before starting with this DevOps project, ensure you have the following prerequisites:
- An AWS Account
- Programmatic access set up with AWS CLI configured
- Python 3 installed
- Docker installed
- Kubectl installed
- A code editor (e.g., VScode)

## Overview

This project involves creating a monitoring application in Python using Flask and Psutil, deploying it locally, containerizing it using Docker, and then deploying it to AWS EKS (Elastic Kubernetes Service).

### Steps

1. **Creating Monitoring Application**

   - Develop a Python application using Flask for web framework and Psutil for system monitoring.

2. **Running the Application Locally**

   - Ensure Python dependencies are installed (`pip3 install -r requirements.txt`).
   - Run the application locally on port 5000: `python app.py`.

3. **Containerizing the Application using Docker**

   - Write a Dockerfile to specify how to build the Docker image.

4. **Writing Dockerfile**

   - Create a Dockerfile to define the environment and dependencies needed for running the application.

   ```dockerfile
   FROM python:3.9-slim-buster

   WORKDIR /app

   COPY requirements.txt .

   RUN pip3 install --no-cache-dir -r requirements.txt

   COPY . .

   ENV FLASK_RUN_HOST=0.0.0.0

   EXPOSE 5000

   CMD ["flask", "run"]
   ```

5. **Building Docker Image from Dockerfile**

   - Build the Docker image using the Dockerfile

6. **Running Docker Container from Docker Image**

   - Run the Docker container from the built image

7. **Creating ECR and Pushing Image to the Repo**

   - Use Python Boto3 to create an ECR repository.
   - Push the Docker image to the ECR repository.

8. **Creating EKS Cluster and Nodes**

   - Set up an AWS EKS cluster with worker nodes.

9. **Creating Kubernetes Deployments and Service using Python**

   - Use Kubernetes Python Client to create Kubernetes Deployments and Services.

10. **Port Forwarding and Exposing Kubernetes Application**

    - Port forward the Kubernetes service to access the application deployed on Kubernetes pod.

