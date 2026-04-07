pipeline {
    agent any

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
                bat 'docker rm -f space || exit /b 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run --name my-devops-container space'
            }
        }

        stage('Docker Hub Login Check') {
            steps {
                bat 'docker info'
            }
        }

        stage('Tag Image') {
            steps {
                bat 'docker tag space nikhilabba12/space:latest'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push nikhilabba12/space:latest'
            }
        }
    }
}