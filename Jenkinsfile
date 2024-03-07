pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent'
            yamlFile 'pod.yaml'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from SCM
                git 'https://github.com/Daudkhan1/my-jenkins-agent.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Change directory to the repository where your Dockerfile is located
                dir('path/to/your/dockerfile/directory') {
                    // Build your Docker image
                    sh 'docker build -t my-image .'
                }
            }
        }
        stage('Scan Docker Image') {
            steps {
                // Scan your Docker image with Trivy
                sh 'trivy --cache-dir /root/.cache/trivy --exit-code 0 my-image'
            }
        }
    }
}
