pipeline {
    agent any

    environment {
        DOCKERHUB_CREDS = credentials('dockerhub-creds')
        IMAGE_NAME = 'nikhilabba12/space:latest'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t space .'
            }
        }

        stage('Docker Login') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
            bat '@echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
        }
    }
}

stage('Tag Image') {
    steps {
        bat 'docker tag my-devops-app nikhilabba12/my-devops-app:latest'
    }
}

stage('Push Image') {
    steps {
        bat 'docker push nikhilabba12/my-devops-app:latest'
    }
}