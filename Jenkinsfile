pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/bhavanagowda28/java-test-2.git'
            }
        }

        stage('Compile') {
            steps {
                sh 'javac App.java'
            }
        }

        stage('Run App') {
            steps {
                sh 'java App'
            }
        }
    }
}
