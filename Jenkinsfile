pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing deltachat desktop communicator...'
            }
        }
    }
    post {
        always {
            emailext attachLog: false, body: '', subject: 'Deltachat pipeline result', to:'piotrekapriasz@gmail.com'
        }
    }
}