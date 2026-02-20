
pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/bhavanagowda28/java-test-2.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run App') {
            steps {
                sh 'java -jar target/*.jar'
            }
        }
    }
}