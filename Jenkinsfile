pipeline {
    agent any
    stages {
        stage('No-op') {
            steps {
                sh 'ls'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
    post {
    failure {
        mail to: 'omar_esharie@hotmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
    }
}

post {
    success {
        mail to: 'omar_esharie@hotmail.com',
             subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
             body: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
    }
}
}






