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
                bat 'docker build -t my-devops-app .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker rm -f my-devops-container || exit /b 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run --name my-devops-container my-devops-app'
            }
        }

        stage('Docker Hub Login Check') {
            steps {
                bat 'docker info'
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