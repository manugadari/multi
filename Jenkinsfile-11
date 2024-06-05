pipeline {
    agent any

    stages {
    
        stage('Snyk Authentication') {
            steps {
                // Authenticate with Snyk using credentials stored in Jenkins
                withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
                    sh 'snyk auth ${SNYK_TOKEN}'
                }
            }
        }
        stage('Snyk Test') {
            steps {
                // Run Snyk tests with a severity threshold
                sh 'snyk test --severity-threshold=high'
            }
        }
    }

    post {
        always {
            // Clean up workspace after the build
            cleanWs()
        }
    }
}
