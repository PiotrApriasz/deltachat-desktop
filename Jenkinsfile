pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing deltachat desktop communicator...'
                script {
                    subject = "Successfull build!"
                }
            }
        }
    }
    post {
        always {
            emailext attachLog: true, body: '', subject: "${subject}", to:'demik534@gmail.com'
        }
    }
}