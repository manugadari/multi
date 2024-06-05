pipeline {
    agent any

    tools {
        maven 'MAVEN' // Refers to a global tool configuration for Maven called 'maven-3.6.0'
    }

    environment {
        SNYK_TOKEN = credentials('SNYK_TOKEN')
    }

    stages {
 
        stage('Snyk Test using Snyk CLI') {
            steps {
                sh './snyk code test'
            }
        }

        stage('Snyk Monitor using Snyk CLI') {
            steps {
                sh './snyk monitor --org=manugadari'
            }
        }
    }
}
