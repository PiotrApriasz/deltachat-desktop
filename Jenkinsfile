pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building deltachat desktop communicator...'
                sh 'docker-compose build buildsection'
            }
            post {
                success {
                    echo 'Successfull Build!'
                    script {
                        subject = "Succesfull Build!"
                    }
                }
                failure {
                    echo 'FAILURE Build!'
                    script {
                        subject = "Failure Build!"
                    }
                }
            }
        }
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
                        subject = "Successfull Test!"
                    }
                }
                failure {
                    echo "Failure Test!"
                    script {
                        subject = "Failed Test!"
                    }
                }
            }
        }
    }
    post {
        always {
            emailext attachLog: true, body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
            subject: "${subject} [${env.BUILD_NUMBER}]", to:'piotrekapriasz@gmail.com'
        }
    }
}