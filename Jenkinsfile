pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }


        // Stage3 : Publish to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'WEB-APP-TFG', classifier: '', file: 'target/WEB-APP-TFG-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: 'f3e6c4d1-9179-4a7c-bfe8-98f9f4a57044', groupId: 'com.WEB-APP-TFG', nexusUrl: '172.20.10.160:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'TFG-DALG-SNAPSHOT', version: '0.0.4-SNAPSHOT'
            }
        }

        // Stage2 : Deploying
        stage ('Deploy'){
            steps {
                echo ' deploying......'

            }
        }

        // Stage3 : Publish the source code to Sonarqube
        stage ('Sonarqube Analysis'){
            steps {
                echo ' Source code published to Sonarqube for SCA......'
                /*withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
                     sh 'mvn sonar:sonar'
                }*/
            }
        }  
    }
}
