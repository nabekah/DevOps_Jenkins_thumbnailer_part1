pipeline {
    agent any
    tools {
        maven "3.6.2"
        
    }
    stages {
        stage('pull from gitlab'){
            steps{
                git branch: "${params.VERSION_BRANCH}" , credentialsId: 'feefb181-a57e-4003-9f28-9487d93d1122', url: 'http://34.222.28.140:8086/ekow_developer/thumbnailer-imageio-extensions.git'
            }
        }
        stage('Build') {
            steps {
                
                sh 'mvn install'
                
            }
        }
     }
    post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: '*/test-reports/.xml'
      )
      }
   } 
}