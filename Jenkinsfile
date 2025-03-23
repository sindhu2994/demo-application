pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                script {
                    def jdkPath = tool name: 'JDK21', type: 'jdk'
                    def mavenPath = tool name: 'Maven3.9.9', type: 'maven'

                    if (!fileExists("${jdkPath}/bin/java")) {
                        error("JDK21 is not installed.")
                    }
                    if (!fileExists("${mavenPath}/bin/mvn")) {
                        error("Maven3.9.9 is not installed.")
                    }
                }
            }
        }

        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/sindhu2994/demo-application.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh "${tool 'Maven3.9.9'}/bin/mvn clean install"
            }
        }

        stage('Test') {
            steps {
                sh "${tool 'Maven3.9.9'}/bin/mvn test"
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