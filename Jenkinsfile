pipeline {
    agent any

    tools {
        jdk 'java17'
        maven 'Maven3'
    }

    environment {
        MAVEN_REPO = "/var/lib/jenkins/.m2"
        MAVEN_OPTS = "-Dmaven.repo.local=${MAVEN_REPO}"
    }

    stages {

        stage("Cleanup Workspace") {
            steps {
                sh 'rm -rf target || true'
            }
        }

        stage("Checkout from SCM") {
            steps {
                git(
                    branch: 'main',
                    credentialsId: 'github',
                    url: 'https://github.com/Mohamed0emad/register-app-cicd.git'
                )
            }
        }

        stage("Build & Test") {
            steps {
                sh '''
                mvn -B -T 1C clean package test
                '''
            }
        }
    }
}
