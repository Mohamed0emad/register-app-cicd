pipeline {
    agent any

    tools {
        jdk 'java17'
        maven 'Maven3'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout SCM') {
            steps {
                git branch: 'main',
                    credentialsId: 'github',
                    url: 'https://github.com/Mohamed0emad/register-app-cicd.git'
            }
        }

        stage('Build All Modules') {
            steps {
                sh 'mvn -B clean package'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
