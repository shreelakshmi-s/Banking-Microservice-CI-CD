# Banking Microservice CI/CD Pipeline

A CI/CD pipeline for a Spring Boot banking microservice, built as a DevOps capstone project. The goal was to move from a slow-to-release monolith to a microservice that can be built, tested and deployed automatically.

## Pipeline flow

```
Git push → GitHub webhook → Jenkins → Maven build & test → Docker image → Docker Hub → Deploy to AWS EC2
```

## Tools used
- **Source control:** Git, GitHub
- **CI/CD:** Jenkins (Declarative Pipeline / Jenkinsfile)
- **Build:** Maven (`clean package` creates the JAR)
- **Containers:** Docker (Dockerfile, Docker Hub registry)
- **Orchestration:** Kubernetes (NodePort service)
- **Cloud:** AWS EC2 (Ubuntu)

## How it works
1. A developer pushes code to GitHub, and a **webhook** triggers the Jenkins pipeline.
2. Jenkins builds and tests the code with **Maven**. If a stage fails, the pipeline stops and shows the error in the console output.
3. A **Docker image** is built from the Dockerfile and pushed to **Docker Hub**.
4. The application is deployed to **AWS EC2**, and Kubernetes runs the containers.

## Repository contents
- `Jenkinsfile`: pipeline definition
- `Dockerfile`: image for the Spring Boot app (Java 21 JRE base image)
- `k8s/`: Kubernetes Deployment and Service YAML files

## What I learned
- Fixed a Java version mismatch between Jenkins (Java 21) and the Maven build (Java 17)
- Handled low memory on small EC2 servers by configuring swap
- Stored the GitHub SSH key in Jenkins credentials instead of in the code
- Troubleshot failed builds from the Jenkins console output


