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
                container('kaniko') {
                    sh "mkdir -p /workspace/src"
                    sh "cd /workspace/src"
                    git 'https://github.com/Daudkhan1/my-jenkins-agent.git'
                    sh "cd /workspace/src"
                    sh "ls -l" // Ensure the Dockerfile is present
                    sh "kaniko --context=/workspace/src --dockerfile=/workspace/src/Dockerfile --destination=your-image-name:latest"
                }
            }
        }
        stage('Scan Docker Image') {
            steps {
                container('trivy') {
                    sh "trivy your-image-name:latest"
                }
            }
        }
    }
}
