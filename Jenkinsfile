pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT     = 'expense'
        COMPONENT   = 'backend'
        ENVIRONMENT = 'dev'
        DEPLOY_TO   = "production"
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
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
                sh 'echo "Hello, this is build"'
                echo "Project: $PROJECT"
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Hello, this is test"'
            }
        }
        stage('Deploy') {
            when {
                environment name: 'DEPLOY_TO', value: 'production'
            }
           /*  input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            } */
            steps {
                echo "Deploying..."
            }
        }
        stage('parallel stages') {
            parallel {
                stage('stage-1') {
                    steps {
                        sh 'echo "Hello, this is stage-1"'
                        sleep 15
                    }
                }
                stage('stage-2') {
                    steps {
                        sh 'echo "Hello, this is stage-2"'
                        sleep 15
                    }
                }
            }
        }
    }
    post {
        always {
            echo "I will always run this build"
        }
        failure {
            echo "I will run pipeline is failed"
        }
        success {
            echo "I will run pipeline is success"
        }
    }
}
