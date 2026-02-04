pipeline {
    agent any

    tools {
        jdk 'java17'
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -B'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test -B'
            }
        }
    }
}
