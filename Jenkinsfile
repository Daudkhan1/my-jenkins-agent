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
                    sh "mkdir -p /workspace/src"
                    sh "cd /workspace/src"
                    git 'https://github.com/Daudkhan1/my-jenkins-agent.git'
                    sh "cd /workspace/src"
                    sh "ls -l" // Ensure the Dockerfile is present
                    sh "docker build -t my-latest-image /workspace/src"
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

