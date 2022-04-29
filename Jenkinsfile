pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing deltachat desktop communicator...'
                sh 'docker-compose  build  testsection'
                sh 'docker-compose  up testsection'
            }
            post {
                success {
                    echo "Success Test!"
                    script {
                        subject = "Successfull build!"
                    }
                }
                failure {
                    echo "Failure Test!"
                    script {
                        subject = "Failed build!"
                    }
                }
            }
        }
    }
    post {
        always {
            emailext attachLog: true, body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
            subject: "${subject}", to:'piotrekapriasz@gmail.com'
        }
    }
}