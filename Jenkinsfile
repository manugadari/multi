pipeline {
  agent any

  stages {
    stage('sast scan') {
      steps {
         sh './snyk test'
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
