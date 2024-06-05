pipeline {
    agent any

    stages {
    
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/manugadari/multi'
                 def changedFiles = sh(script: "git diff-tree --no-commit-id --name-only -r ${env.CHANGE_ID}", returnStdout: true).trim().split('\n')
                }
            }
        }
}
