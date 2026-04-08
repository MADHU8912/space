pipeline {
    agent any

    stages {
        stage('Docker Login') {
            steps {
                script {
                    bat 'docker login -u nikhilabba12 -p YOUR_TOKEN'
                }
            }
        }

        stage('Build Image') {
            steps {
                script {
                    bat 'docker build -t nikhilabba12/space:latest .'
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    bat 'docker push nikhilabba12/space:latest'
                }
            }
        }
    }
}