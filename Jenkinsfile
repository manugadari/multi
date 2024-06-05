pipeline {
  agent any
  
   stages {
     
    stage('Authorize Snyk CLI') {
            steps {
                withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
                    sh 'snyk auth ${SNYK_TOKEN}'
                }
            }

    stage('Snyk SAST test using Snyk CLI') {
            steps {
                sh 'snyk code test'
            }
        }
    stage('Snyk SCA using Snyk CLI') {
            steps {
                sh 'snyk test'
      }
    }
 }
}
}
