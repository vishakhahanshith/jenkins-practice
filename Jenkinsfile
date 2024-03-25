pipeline {
    //agent any

    agent { node { label 'AGENT-1' } }
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    // triggers{
    //     cron('* * * * *')
    // }
    environment {
        USER = 'sivakumar'
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password') 
    }  
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                //sh 'ls -ltr'
                //sh 'pwd'
                sh '''
                   ls -ltr
                   pwd
                   //echo "Hello Script"
                   echo "Hello from GitHub Push webhook event"
                   printenv
                '''
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
        stage('Example') {
            environment {
                AUTH = credentials('ssh-auth')
            }
            steps {
                sh 'printenv'
                
            }
        }
        stage('Params') {
        steps {
            echo "Hello ${params.PERSON}"
            echo "Biography: ${params.BIOGRAPHY}"
            echo "Toggle: ${params.TOGGLE}"
            echo "Choice: ${params.CHOICE}"
            echo "Password: ${params.PASSWORD}"
        }
    }

    stage('Input') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
        stage('PROD Deploy'){
            when {
                environment name: 'USER', value: 'sivakumar'
            }
            steps{
                echo "deploying to PROD"
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
