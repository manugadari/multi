pipeline {
    agent any

    stages {
    
        stage('Git checkout') {
            steps {
                git branch: '', url: 'https://github.com/manugadari/multi'
                sh'git diff master...feature'
            }
         }
    }
}
