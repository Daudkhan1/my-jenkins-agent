pipeline {
    agent { label 'jenkins-slave' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm: [
                    $class: 'GitSCM',
                    userRemoteConfigs: [[
                        url: 'https://github.com/Daudkhan1/my-jenkins-agent.git',
                    ]],
                ]
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "docker build -t my-latest-image ."
            }
        }
        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-id', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh "docker tag my-latest-image $DOCKER_USER/my-latest-image:main"
                    sh "docker push $DOCKER_USER/my-latest-image:main"
                }
            }
        }
    }
}
