pipeline {
    //agent any

    agent { node { label 'AGENT-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                //sh 'ls -ltr'
                //sh 'pwd'
                sh '''
                   ls -ltr
                   pwd
                   echo 'Hello Script'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                // error 'This is failed'
            }
        }
    }

    post {
        always {
            echo 'I will always run whether job is success or not'
        }
        success {
            echo 'I will run only when the job is success'
        }
        failure {
            echo 'I will run when the job is failure'
        }
    }
}