pipeline {
    //agent any

    agent { node { label 'AGENT-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
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
                sh 'ls -ltr'
                sh 'pwd'
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