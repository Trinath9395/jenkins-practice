pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'expense'
        COMPONENT = 'backend'
    }
    options {
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello, this is build"'
                echo "Project: $PROJECT"
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
