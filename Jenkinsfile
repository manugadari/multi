pipeline {
    agent any

    stages {

         stage('Snyk Test using Snyk CLI') {
            steps {
                sh 'snyk -v'
            }
        }

    }
}
