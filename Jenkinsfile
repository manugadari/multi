pipeline {
  agent any
  tools {
        maven 'MAVEN' // Refers to a global tool configuration for Maven called 'maven-3.6.0'
    }

    // Pull your Snyk token from a Jenkins encrypted credential
    // (type "Secret text"... see https://jenkins.io/doc/book/using/using-credentials/#adding-new-global-credentials)
    // and put it in temporary environment variable for the Snyk CLI to consume.
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
