pipeline {
  agent any
    stages {
        stage('Authorize Snyk CLI') {
            steps {
                withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
                    sh 'snyk auth ${SNYK_TOKEN}'
                }
             }
          }
         stage('SAST SCAN') {
            steps {
                sh 'snyk code test --severity-threshold>high '
                }
            }
        }
    }
