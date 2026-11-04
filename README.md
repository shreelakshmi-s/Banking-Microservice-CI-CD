# Banking Web App: CI/CD Pipeline Project

Banking microservice built and deployed as part of the DevOps & Cloud Computing course at Paper Live Learning. Forked from the course project (PL-DevOps-Cloud-2705/BankingWebApp). The goal was to move from a monolith to a microservice that is built, containerized and deployed automatically.

## What I did
- Set up a Jenkins pipeline on AWS EC2: GitHub webhook, Maven build, Docker image build and push, deployment
- Containerized the app using the included `Dockerfile`
- Deployed it to a Kubernetes cluster (kubeadm, 3 nodes) using `bankingdeploy.yaml`, exposed with a NodePort service
- Fixed real issues: Java version mismatch (Jenkins on Java 21, Maven build on Java 17), low memory on small EC2 servers (added swap), and Kubernetes node join errors

## Tools
Git/GitHub, Jenkins, Maven, Docker, Kubernetes, AWS EC2 (Ubuntu), Linux

## Repository contents
- `Dockerfile`: image definition
- `bankingdeploy.yaml`: Kubernetes deployment
- `pom.xml`, `src/`: Maven build and application code

## Pipeline flow
`Git push → Jenkins → Maven build → Docker image → Deploy to Kubernetes`
