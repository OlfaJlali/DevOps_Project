# DevOps Backend with Spring Boot

This project is a backend application developed using the Spring Boot framework for a DevOps pipeline. The application is designed to seamlessly integrate with various DevOps tools to automate processes such as continuous integration, testing, deployment, and monitoring. The key components of this project include Spring Boot, Jenkins, JUnit, SonarQube, Nexus, Docker, Prometheus, and Grafana
## Setup

Clone the repository:
```bash
git clone https://github.com/OlfaJlali/DevOps_Project.git
cd devops-backend
```
Build the project:
```bash
mvn clean install
```


## Usage

#### 1- Push changes to the repository to trigger the Jenkins build.
#### 2- Monitor the build status in Jenkins.
#### 3-Review code quality in SonarQube.
#### 4-Deploy the application using Docker and Nexus.
#### 5-Monitor application metrics in Grafana.

## Features
The core of the project is a robust backend application developed with the Spring Boot framework, providing a scalable and efficient foundation.

### Jenkins Integration with Webhook: 
The application is integrated with Jenkins to automate the continuous integration and deployment processes. Jenkins is configured with a webhook to trigger builds automatically whenever changes are pushed to the repository.

### Automated Testing with JUnit: 
The codebase is thoroughly tested using JUnit, ensuring the reliability and correctness of the application. Jenkins is configured to run these tests automatically during the continuous integration process.

### Code Quality Analysis with SonarQube:
SonarQube is utilized for static code analysis to maintain code quality. The integration with Jenkins ensures that code quality is continuously monitored throughout the development lifecycle.

### Artifact Repository with Nexus: 
The project artifacts are stored in Nexus, a repository manager, to facilitate versioning, distribution, and deployment of the application.

### Containerization with Docker: 
The application is containerized using Docker, providing a consistent and isolated environment for deployment. Docker images are created and stored in Nexus for seamless deployment.

### Monitoring with Prometheus and Grafana: 
The application is monitored using Prometheus for collecting metrics, and Grafana for visualizing these metrics. This ensures real-time visibility into the performance and health of the application.

