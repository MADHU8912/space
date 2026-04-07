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
                bat '@echo %DOCKERHUB_CREDS_PSW% | docker login -u %DOCKERHUB_CREDS_USR% --password-stdin'
            }
        }

        stage('Tag Image') {
            steps {
                bat 'docker tag space %IMAGE_NAME%'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push %IMAGE_NAME%'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
    }
}