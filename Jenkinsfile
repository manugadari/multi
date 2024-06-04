pipeline {
  agent any
  
    environment {
        SNYK_TOKEN = credentials('SNYK_API_TOKEN')
    }


  stages {
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
