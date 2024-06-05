pipeline {
    agent any

    environment {
        // Define environment variables
        BRANCH_NAME = 'your-branch-name' // Specify the branch name you want to scan
    }

    stages {
        stage('Checkout Branch') {
            steps {
                // Checkout the specified branch
                script {
                    checkout([$class: 'GitSCM', branches: [[name: "*/${BRANCH_NAME}"]],
                              userRemoteConfigs: [[url: 'https://your-repo-url.git']]])
                }
            }
        }
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
