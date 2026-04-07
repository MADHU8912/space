stage('Docker Login') {
    steps {
        withCredentials([usernamePassword(
            credentialsId: 'dockerhub-creds',
            usernameVariable: 'DOCKER_USER',
            passwordVariable: 'DOCKER_PASS'
        )]) {
            bat '''
docker logout || exit /b 0
echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin
'''
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