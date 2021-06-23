pipeline {
    agent any
    environment {
        LC_ALL = 'en_US.UTF-8'
        LANG    = 'en_US.UTF-8'
        LANGUAGE = 'en_US.UTF-8'
        VAULT_ADDR='http://127.0.0.1:8200'
        VAULT_TOKEN='s.XSDKPQhD8C0hgwWNU0FasD2S'

    }
    stages {

        stage('Prepare_certs') {
            steps {
                sh "pwd"
                dir('/Users/x451868/Documents/formula1App/certsVault/') {
                    sh 'vault kv get -field=provisionFile secret/provision | base64 --decode >f1demoAppStore-3.mobileprovision'
                    sh 'vault kv get -field=distributionFile secret/distribution | base64 --decode >distributionB.p12' 
                }
            } 
        }
        
        stage('SonarQ') {
            steps {
                sh "pwd"
                dir('/Users/x451868/Documents/formula1App') {
                    sh 'fastlane sonarQ' 
                }
            } 
        }

        // stage('Test') {
        //     steps {
        //         echo 'Testing..'
        //     }
        // }

        stage('Deploy_to_appCenter') {
            steps {
                dir('/Users/x451868/Documents/formula1App') {
                    sh 'fastlane distribute_to_appCenter' 
                }
            }
        }

        stage('Remove_certs') {
            steps {
                dir('/Users/x451868/Documents/formula1App/certsVault/') {
                    sh 'rm f1demoAppStore-3.mobileprovision' 
                    sh 'rm distributionB.p12' 
                }
            }
        }

    }
}
