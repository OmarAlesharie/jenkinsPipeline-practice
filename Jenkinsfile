pipeline {
    agent any
    stages {
        stage('Deploy - Staging') {
            steps {
                sh 'echo "deploy staging"'
                sh 'echo "run-smoke-tests"'
            }
        }

        stage('Sanity check') {
            agent none
            steps {
                timeout(time: 10, unit: 'MINUTES') {
                    input "Does the staging environment look ok?"
                }
            }
        }

        stage('Deploy - Production') {
            steps {
                sh 'echo "deploy production"'
            }
        }
    }
}
