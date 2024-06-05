pipeline {
    agent any

    // Install the Jenkins tools you need for your project / environment
    tools {
        maven 'MAVEN' // Refers to a global tool configuration for Maven called 'maven-3.6.0'
    }

    // Pull your Snyk token from a Jenkins encrypted credential
    // (type "Secret text"... see https://jenkins.io/doc/book/using/using-credentials/#adding-new-global-credentials)
    // and put it in temporary environment variable for the Snyk CLI to consume.
    environment {
        SNYK_TOKEN = credentials('SNYK_TOKEN')
    }

    stages {

        
        stage('Snyk Test using Snyk CLI') {
            steps {
                sh './snyk test'
            }
        }

        // Capture the dependency tree for ongoing monitoring in Snyk.
        // This is typically done after deployment to some environment (ex staging, test, production, etc).
        stage('Snyk Monitor using Snyk CLI') {
            steps {
                // Use your own Snyk Organization with --org=<your-org>
                sh './snyk monitor --org=demo-applications'
            }
        }
    }
