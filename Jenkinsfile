pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'expense'
        COMPONENT = 'backend'
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 1, unit: 'HOURS')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello, this is build"'
                echo "Project: $PROJECT"
                sleep 15
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Hello, this is test"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Hello, this is deploy"'
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
