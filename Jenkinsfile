pipeline {
    agent any

    stages {
    
        stage('Git checkout') {
            steps {
                sh 'git fetch --no-tags'
                def changedFiles = sh(script: "git diff-tree --no-commit-id --name-only -r ${env.CHANGE_ID}", returnStdout: true).trim().split('\n')
                }
            }
        }
}
