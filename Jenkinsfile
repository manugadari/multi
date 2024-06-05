pipeline {
    agent any

    stages {

       stage('Authorize Snyk CLI') {
            steps {
                withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
                    sh 'snyk auth ${SNYK_TOKEN}'
                }
            }

        stage('Git Clone') {
            steps {
                git url: 'https://github.com/jeff-snyk-demo/testproject-java-maven.git'
                sh 'ls -la'
            }
        }

        stage('SAST SCAN') {
            steps {
                sh 'snyk code test'
                }
            }
       }
    }
