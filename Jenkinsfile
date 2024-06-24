pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
               docker {
                image 'node:18-alpine'
                reuseNode true
               } 
            }
            steps {
                sh '''
                  ls -la
                  node --version
                  npm --version
                  npm ci
                  npm run build
                  '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                echo "TEST STAGE"
                touch build/index.html
                echo Testfile >> build/index.html
                npm test
                '''
            }
        }
    }
}