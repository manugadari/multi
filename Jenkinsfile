pipeline {
    agent any

    stages {
    
        stage('Git checkout') {
            steps {
                sh 'git fetch --no-tags'
                sh 'git fetch origin' 
                sh 'git diff master feature-2 ./diff_test.txt'
                 }
            }
        }
}
