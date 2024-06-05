pipeline {
    agent any

    stages {
    
        stage('Git checkout') {
            steps {
                sh 'git fetch origin' 
                sh 'git diff master -- feature-2'
                 }
            }
        }
}
