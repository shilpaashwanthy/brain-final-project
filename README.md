# Brain Final Project – AWS CI/CD Pipeline with EKS

## Project Overview

This project demonstrates a complete **CI/CD pipeline on AWS** that automatically builds and deploys an application using containerization and Kubernetes.

The pipeline integrates **GitHub, AWS CodeBuild, Amazon ECR, Docker, and Amazon EKS** to automate the process from source code to deployment.

When code is pushed to GitHub, AWS services automatically build a Docker image, push it to Amazon ECR, and deploy the application to an EKS Kubernetes cluster.

---

## Architecture

GitHub → AWS CodeBuild → Docker Build → Amazon ECR → Amazon EKS → LoadBalancer → Application

---

## Technologies Used

* AWS CodeBuild
* AWS ECR (Elastic Container Registry)
* AWS EKS (Elastic Kubernetes Service)
* Docker
* Kubernetes
* GitHub
* Nginx (sample web application)

---

## Project Workflow

1. **Source Code Management**

   * Application code and configuration files are stored in a GitHub repository.

2. **Build Process**

   * AWS CodeBuild triggers when the repository is connected.
   * The build process follows instructions in the `buildspec.yml` file.

3. **Docker Image Creation**

   * CodeBuild builds a Docker image using the `Dockerfile`.

4. **Push to Amazon ECR**

   * The Docker image is tagged and pushed to Amazon ECR.

5. **Deployment to EKS**

   * Kubernetes deployment files create pods running the application.
   * A LoadBalancer service exposes the application to the internet.

---

## Project Structure

```
brain-final-project
│
├── Dockerfile
├── buildspec.yml
├── deployment.yaml
├── service.yaml
└── README.md
```

---

## File Descriptions

### Dockerfile

Defines the Docker container used to run the application.

Example:

```
FROM nginx:latest
COPY . /usr/share/nginx/html
EXPOSE 80
```

### buildspec.yml

Used by AWS CodeBuild to build the Docker image and push it to Amazon ECR.

### deployment.yaml

Kubernetes configuration file that creates pods running the application in EKS.

### service.yaml

Exposes the application using a Kubernetes LoadBalancer.

---

## Steps to Run the Project

### Step 1 – Create ECR Repository

Create an Amazon ECR repository to store the Docker image.

### Step 2 – Setup CodeBuild

Create a CodeBuild project and connect it to the GitHub repository.

### Step 3 – Add buildspec.yml

Place the `buildspec.yml` file in the root directory of the repository.

### Step 4 – Build Docker Image

CodeBuild builds the Docker image and pushes it to Amazon ECR.

### Step 5 – Create EKS Cluster

Create an EKS cluster and configure kubectl access.

### Step 6 – Deploy Application

Apply the Kubernetes configuration files:

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### Step 7 – Access Application

Use the LoadBalancer URL to access the deployed application.

---

## Expected Output

After deployment:

* Kubernetes pods will be running in the EKS cluster.
* The application will be accessible through an AWS LoadBalancer.

---

## Learning Outcomes

This project demonstrates:

* CI/CD pipeline implementation on AWS
* Containerization using Docker
* Image management with Amazon ECR
* Kubernetes deployment with Amazon EKS
* Automation using AWS CodeBuild

---

## Author

Shilpa
DevOps / Cloud Project
