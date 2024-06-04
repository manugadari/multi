pipeline {
  agent any
  

  stages {
    
    stage('Authorize Snyk CLI') {
            steps {
                withCredentials([string(credentialsId: 'SNYK_API_TOKEN', variable: 'SNYK_API_TOKEN')]) {
                    sh 'snyk auth ${SNYK_API_TOKEN}'
                }
            }
        }

    stage('Snyk Test using Snyk CLI') {
            steps {
                sh './SNYK test'
            }
        }
    stage('Test') {
      steps {
        echo 'Testing...'
        
          snykSecurity failOnError: false, failOnIssues: false, severity: 'critical', snykInstallation: 'SNYK', snykTokenId: 'SNYK_API_TOKEN'
        
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }
  }
}
