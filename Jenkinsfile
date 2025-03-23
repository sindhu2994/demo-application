pipeline {
    agent any

    tools {
            jdk 'JDK21'
            maven 'Maven3.9.9'
        }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/sindhu2994/demo-application.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to server...'
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}