pipeline {
    agent any
    tools {
        maven '3.6.2'
        
        
        
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    env | grep -e PATH -e JAVA_HOME
                    which java
                    java -version
                    mvn --version
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('pull from gitlab'){
            steps{
                git branch: "main" , credentialsId: 'feefb181-a57e-4003-9f28-9487d93d1122', url: 'http://34.222.28.140:8086/ekow_developer/thumbnailer-imageio-extensions.git'
            }
        }
        stage('Build') {
            steps {
                
                sh 'mvn -Dmaven.test.failure.ignore=true install'
                
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