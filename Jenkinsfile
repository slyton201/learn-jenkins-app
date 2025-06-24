pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:22.16.0-alpine3.22'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    npm config rm proxy 
                    npm config rm https-proxy --tried removing npm proxy 
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
