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
                // Change directory to where your Dockerfile is located
                dir('path/to/your/dockerfile/directory') {
                    // Build your Docker image
                    sh 'docker build -t your-image-name .'
                }
            }
        }
        // Add more stages for additional steps in your pipeline if needed
    }
}
