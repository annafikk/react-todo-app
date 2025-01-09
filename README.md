# Modernization of Monolithic React Application Into Cloud-Native Architecture Using Containerization

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Architecture](#architecture)
- [Setup and Installation](#setup-and-installation)
- [How to Run](#how-to-run)
- [CI/CD Workflow](#cicd-workflow)
- [Scaling and Monitoring](#scaling-and-monitoring)
- [Conclusion](#conclusion)
- [References](#references)

## Overview
This project transforms a monolithic React To-Do application into a cloud-native architecture using containerization. By leveraging tools like Podman, Red Hat Quay.io, and OpenShift, the application achieves better scalability, CI/CD automation, and real-time monitoring capabilities.

## Features
- **Scalable Architecture**: Automatically scales to handle increased workloads using Horizontal Pod Autoscaler (HPA).
- **Continuous Integration/Continuous Deployment (CI/CD)**: Automates build, push, and deployment using GitHub Actions.
- **Real-Time Monitoring**: Provides insights into application performance through OpenShift Observe.
- **Cloud-Native Transformation**: Containerized using Podman and deployed to OpenShift for orchestration.

## Technologies Used
- **React.js**: Frontend library for building the application.
- **Podman**: For containerizing the application.
- **Red Hat Quay.io**: Secure container image registry.
- **Red Hat OpenShift**: For container orchestration and scaling.
- **GitHub Actions**: CI/CD workflow automation.
- **OpenShift Observe**: Monitoring tools.

## Architecture
The project follows a cloud-native design with the following flow:
1. **Code Push**: Developers push code to the GitHub repository.
2. **CI/CD Pipeline**: GitHub Actions automates build and deployment.
3. **Containerization**: The application is containerized using Podman.
4. **Registry**: Images are stored securely in Red Hat Quay.io.
5. **Deployment**: The application is deployed to OpenShift with auto-scaling enabled.
6. **Monitoring**: Performance metrics and logs are tracked in real-time.

## Setup and Installation
1. Clone this repository:
    ```bash
    git clone https://github.com/Ramadiyandi/react-todo-app.git
    cd react-todo-app
    ```
2. Install dependencies:
    ```bash
    npm install
    ```
3. Build the project:
    ```bash
    npm run build
    ```
4. Containerize the application using Podman:
    ```bash
    podman build -t react-todo-app:latest .
    ```

## How to Run
1. Run the container locally:
    ```bash
    podman run -d -p 8080:8080 react-todo-app:latest
    ```
2. Push the container to Quay.io:
    ```bash
    podman tag react-todo-app:latest quay.io/username/react-todo-app:latest
    podman push quay.io/username/react-todo-app:latest
    ```
3. Deploy to OpenShift:
    ```bash
    oc login --token=YOUR_TOKEN --server=YOUR_OPENSHIFT_SERVER
    oc new-app quay.io/username/react-todo-app:latest
    oc expose svc/react-todo-app
    ```

## CI/CD Workflow
The CI/CD pipeline is defined in `CICD.yml` and automates:
1. **Build and Tag**: Creates a container image using Podman.
2. **Push to Registry**: Stores the image in Red Hat Quay.io.
3. **Deploy to OpenShift**: Updates or creates deployments, services, and routes.

## Scaling and Monitoring
- **Scaling**: The Horizontal Pod Autoscaler (HPA) automatically adjusts pod replicas based on CPU/memory usage.
- **Monitoring**: OpenShift Observe provides dashboards to track CPU, memory, and network usage.

## Conclusion
This project demonstrates the successful modernization of a monolithic application into a scalable and efficient cloud-native solution. The combination of containerization, orchestration, and CI/CD automation ensures robust performance and ease of management.

## References
1. [React To-Do App Repository](https://github.com/ShaifArfan/react-todo-app)
2. [Research Paper](https://docs.google.com/document/d/1V7iSR_2wvI6cnjuCeJMGLV56Lf23rW86EU_uv0cS2Mo/edit?usp=sharing)
3. [Design Thinking](https://www.figma.com/board/mVMpTP78nphIHkzmvQ6pOD/Modernize-Application?node-id=0-1&t=Gc1wWM2gmP6BjVu3-1)
