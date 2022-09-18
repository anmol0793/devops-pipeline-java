pipeline {
    agent any
    environment {
        JAVA_VERSION=11
        DEVOPS_BATCH=AUG2022
    }
    parameters {
        choice(name: 'DEPLOYMENT_ENV',
        choices: ['UAT1', 'UAT2', 'PREPOD'],
        description: 'Select Env for deploy'
        )
        string(name: 'DUMMYSTR',
        description : 'just a dummy value',
        defaultValue:'Anmol')
    }
    triggers { 
        pollSCM('*****')
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
            post {
             always {
                slackSend channel: 'devops', message: 'BUILD COMPLETED'
    
            }
         
        }

}