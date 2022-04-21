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
            mail to: piotrakapriasz@gmail.com, subject: 'Deltachat pipeline result'
        }
    }
}