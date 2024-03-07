pipeline {
    agent {
        kubernetes {
            label 'jenkins-agent'
            yamlFile 'pod.yaml'
        }
    }
    stages {
        stage('Build Docker Image') {
            steps {
                container('docker') {
                    //sh "ls -l /workspace/src" // Ensure the Dockerfile is present
                    sh "docker build -t my-latest-image ."
                }
            }
        }
        stage('Scan Docker Image') {
            steps {
                container('trivy') {
                    sh "trivy my-latest-image"
                }
            }
        }
    }
}


