pipeline {
    agent any

    tools {
        jdk 'java17'
        maven 'Maven3'
    }

    stages {

        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }

        stage("Checkout from SCM") {
            steps {
                git branch: 'main',
                    credentialsId: 'github',
                    url: 'https://github.com/Mohamed0emad/Food-Lover-main.git',
                    shallow: true
                sh "ls -al"
            }
        }

        stage("Build Application") {
            steps {
                sh 'mvn -Dmaven.repo.local=$HOME/.m2/repository clean package'
            }
        }

        stage("Test Application") {
            steps {
                sh 'mvn -Dmaven.repo.local=$HOME/.m2/repository test'
            }
        }

    }
}
