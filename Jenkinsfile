pipeline {
    agent any

    environment {
        DOCKERHUB_CREDS = credentials('dockerhub-creds')
        IMAGE_NAME = 'nikhilabba12/space:latest'
    }

    stages {
        stage('Check Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t space .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker rm -f space-container || exit /b 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d --name space-container space'
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
            bat 'docker logout || exit /b 0'
        }
    }
}