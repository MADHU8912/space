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
                bat 'docker rm -f space-container || exit /b 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run --name space-container space'
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