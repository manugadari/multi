pipeline {
    agent any

    stages {
    
        stage('Git checkout') {
            steps {
                git 'https://github.com/manugadari/multi'
                sh'git diff master--feature'
            }
         }
    }
}
