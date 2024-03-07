pipeline {
    agent {
        kubernetes {
            defaultContainer 'jenkins-agent'
            yamlFile 'pod.yaml'
        }
    }

    stages {
        stage('Checkout') {
            steps {
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
