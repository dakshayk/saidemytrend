 pipeline {
    agent any 
    environment {
       PATH = "/opt/maven/bin:$PATH"
    }
  

    stages {
      
       stage ('build') {

         steps {
            sh 'mvn clean deploy'
         }
       }

       stage ('SonarQube Quality Analysis') {

         environment {
            scannerHome = tool 'dakshayk-sonar-scanner'
         }

         steps {
            WithSonarQubeEnv('dakshayk-sonar-server') {
               sh "${ScannerHome}/bin/sonar-scanner
            } 
         }
       }  
    }
 }
