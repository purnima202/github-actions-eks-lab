# Sweet Crumbs – CI/CD Project

## Project Overview

Sweet Crumbs is a simple static website used to practice CI/CD using GitHub Actions, Docker, Docker Hub and AWS ECS.

## Technologies Used

* Git & GitHub
* GitHub Actions
* Docker
* Docker Hub
* AWS ECS
* AWS IAM
* GitHub OIDC
* AWS CLI

## CI/CD Flow

```text
Feature Branch
     ↓
Pull Request → main
     ↓
CI
     ↓
Docker Build
     ↓
Merge to main
     ↓
CD
     ↓
Docker Build
     ↓
Docker Hub
     ↓
AWS OIDC
     ↓
ECS Deployment
     ↓
Updated Website
```

## CI

When a Pull Request is created or updated:

* Checkout code
* Check project files
* Build Docker image

## CD

After the Pull Request is merged into `main`:

* Build Docker image
* Push image to Docker Hub
* Authenticate to AWS using OIDC
* Trigger ECS deployment

## Docker

The application is containerized using Docker.

## AWS ECS

The application was deployed as a container on Amazon ECS.

GitHub Actions triggers a new ECS deployment after code is merged into `main`.

## GitHub OIDC

GitHub Actions uses OpenID Connect (OIDC) to authenticate with AWS without storing long-term AWS access keys.

## Project Structure

```text
github-actions-eks-lab/
│
├── index.html
├── Dockerfile
└── .github/
    └── workflows/
        └── ci.yml
```

## Result

The CI/CD pipeline was tested by modifying the website and verifying that the updated version was successfully deployed through the pipeline.
