pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh "pwd"
                dir('~//Users/x451868/Documents/formula1App') {
                    sh "pwd"
                    fastlane sonarQ
                }
                sh "pwd"
        } 
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
