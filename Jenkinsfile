pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "spring-boot-demo:${env.BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/spring-boot-ci-cd.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker stop demo || true"
                sh "docker rm demo || true"
                sh "docker run -d --name demo -p 8080:8080 ${DOCKER_IMAGE}"
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful! Access http://<your-server-ip>:8080/hello'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}

