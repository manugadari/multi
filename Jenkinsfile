pipeline {
    agent any

    environment {
        BRANCH_NAME = 'feature-2'   // The branch you want to compare
        BASE_BRANCH = 'master'               // The base branch to compare against
    }

    stages {
        stage('Checkout Branch') {
            steps {
                // Checkout the specified branch
                script {
                    checkout([$class: 'GitSCM', branches: [[name: "*/${feature-2}"]],
                              userRemoteConfigs: [[url: 'https://your-repo-url.git']]])
                }
            }
        }

        stage('Fetch Modified Files') {
            steps {
                // Fetch the latest changes and identify modified files
                script {
                    sh 'git fetch origin'
                    modifiedFiles = sh(script: "git diff --name-only origin/${BASE_BRANCH}...origin/${BRANCH_NAME}", returnStdout: true).trim()
                    if (modifiedFiles) {
                        echo "Modified files:\n${modifiedFiles}"
                    } else {
                        echo "No modified files found between ${BASE_BRANCH} and ${BRANCH_NAME}."
                        currentBuild.result = 'SUCCESS'
                        return
                    }
                }
            }
        }

        stage('Checkout Modified Files') {
            steps {
                // Checkout only the modified files
                script {
                    if (modifiedFiles) {
                        modifiedFiles.split('\n').each { file ->
                            sh "git checkout origin/${BRANCH_NAME} -- ${file}"
                        }
                    }
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
