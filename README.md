# Jenkins CI/CD Docker Demo Project

## Project Overview

This project demonstrates a simple **CI/CD pipeline using Jenkins and Docker**.
The pipeline automatically pulls code from GitHub, builds a Docker image, and deploys the application in a Docker container.

The application is a simple **HTML web page** served using **Nginx inside a Docker container**.

---

## CI/CD Pipeline Flow

GitHub → Jenkins → Docker Build → Docker Container → Web Application

1. Developer pushes code to GitHub
2. Jenkins pipeline pulls the latest code
3. Docker builds an image using the Dockerfile
4. Jenkins runs the container automatically
5. Application becomes accessible in the browser

---

## Project Structure

```
jenkins-devops-project/
│
├── Dockerfile
├── Jenkinsfile
├── index.html
└── README.md
```

---

## Technologies Used

* Jenkins
* Docker
* Git & GitHub
* HTML
* Nginx

---

## Jenkins Pipeline Stages

1. Clone Repository
2. Build Docker Image
3. Stop Old Container
4. Run Docker Container

---

## Jenkinsfile Pipeline

```
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/noormohammad161996-cloud/jenkins-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f jenkins-container || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name jenkins-container jenkins-demo'
            }
        }

    }
}
```

---

## Dockerfile

```
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

---

## Application Output

After the pipeline runs successfully, the application is available at:

http://localhost:8081

The web page displays:

Welcome to Jenkins CI/CD Demo
Project by Noor Mohammad

---

## Author

Noor Mohammad
DevOps Engineer (Learning Phase)

GitHub:
https://github.com/noormohammad161996-cloud

---

## Purpose of This Project

This project was created to demonstrate a **basic DevOps CI/CD pipeline** using Jenkins and Docker for learning and discussion purposes.
