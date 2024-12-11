pipeline{
    agent{
       node{
        label "MAVEN"
       }	
    }
    stages{
        stage("Building Code"){
            steps{
                sh 'mvn clean deploy'
            }
        }
        stage('SonarQube analysis') {
           environment{
             scannerHome = tool 'Gyan-sonarqube_scanner';
            }
            steps{
               withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
               sh "${scannerHome}/bin/sonar-scanner"
               }
            }
        }   
    }
}
