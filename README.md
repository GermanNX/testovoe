# Project Overview

This repository contains the configuration files and scripts necessary to set up a CI/CD pipeline using Jenkins, Docker, and Kubernetes (Minikube). Below is a brief description of each component and instructions on how to use them.

## Ansible Playbook

The Ansible playbook located in `ansible/playbook.yml` installs Jenkins, Docker, and Minikube on an Ubuntu machine.

## Docker

The `docker/` directory contains:
- `Dockerfile`: Builds a Docker image that runs a simple Python "Hello World" script.
- `hello.py`: A simple Python script that prints "Hello World".

## Jenkins

The `jenkins/Jenkinsfile` defines a Jenkins pipeline that builds, tests, and pushes the Docker image to Docker Hub.

## Helm

The `helm/mychart/` directory contains the Helm chart for deploying the Docker image to a Minikube cluster.

## Getting Started

### Prerequisites

- Ansible
- Docker
- Jenkins
- Minikube
- Helm

### Instructions

1. **Set up Ansible**:
    - Run the Ansible playbook to install Jenkins, Docker, and Minikube:
      ```bash
      ansible-playbook -i hosts ansible/playbook.yml
      ```

2. **Build and Push Docker Image**:
    - Create a Jenkins job using the pipeline defined in `jenkins/Jenkinsfile`.

3. **Deploy to Minikube**:
    - Initialize Minikube:
      ```bash
      minikube start --driver=docker
      ```
    - Deploy the Helm chart:
      ```bash
      helm install mychart helm/mychart
      ```

## Repository Structure

```
project-root/
├── ansible/
│   └── playbook.yaml
├── docker/
│   ├── Dockerfile
│   └── hello.py
├── jenkins/
│   └── Jenkinsfile
└── helm-chart
        ├── Chart.yaml
        ├── values.yaml
        └── templates/
            ├── deployment.yaml
            └── service.yaml
└── README.md
```

### Contributing

Please submit issues and pull requests for any improvements or fixes.

### License

This project is licensed under the MIT License.
