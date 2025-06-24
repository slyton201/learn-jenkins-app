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
                    ping -c 4 registry.npmjs.org || true
                    curl -I https://registry.npmjs.org || true
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
