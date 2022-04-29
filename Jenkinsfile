pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing deltachat desktop communicator...'
                sh 'ls'
                sh 'docker-compose  build  test-agent'
                sh 'docker-compose  up --force-recreate -d test-agent'
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