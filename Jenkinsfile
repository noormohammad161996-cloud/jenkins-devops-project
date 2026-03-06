pipeline {
agent any

```
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
```

}
