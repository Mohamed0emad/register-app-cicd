pipeline {
    agent any

    tools {
        jdk 'java17'
        maven 'Maven3'
    }

    environment {
        MAVEN_OPTS = "-Dmaven.repo.local=$HOME/.m2/repository"
    }

    stages {

        stage("Cleanup Workspace") {
            steps {
                cleanWs(
                    deleteDirs: true,
                    disableDeferredWipeout: true
                )
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

        stage("Build Application") {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage("Test Application") {
            steps {
                sh 'mvn -B test'
            }
        }
    }
}
