pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from SCM
                git 'https://github.com/Daudkhan1/my-jenkins-agent.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "ls -l $WORKSPACE/src" // Ensure the Dockerfile is present
                sh "docker build -t my-latest-image $WORKSPACE/src"
            }
        }
        stage('Scan Docker Image') {
            steps {
                sh "docker scan my-latest-image"
            }
        }
    }
}
