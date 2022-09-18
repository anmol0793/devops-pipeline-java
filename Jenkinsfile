pipeline {
    agent any
    environment {
        JAVA_VERSION="11"
        DEVOPS_BATCH="AUG2022"
}
   
  
    options {
     buildDiscarder logRotator(artifactDaysToKeepStr: '2', artifactNumToKeepStr: '2', daysToKeepStr: '2', numToKeepStr: '2')
     }
     tools {
     jdk 'jdk11'
     maven 'Maven'
     }

     stages {
        stage('Checkout') {
            steps{
                checkout scm
             }
        }    
         stage('Compile'){
            steps{
                sh 'mvn compile'
             }
        }
     }
        post {
             always {
                slackSend channel: 'devops', message: 'BUILD COMPLETED'
    
            }
         
        }

}