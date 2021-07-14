pipeline{

    agent any
    tools{

        maven 'maven'
    }

    stages {

        stage ('Build'){

           steps {
                sh 'mvn clean install package'
            }
        }
        
        stage ('Test'){
            steps {

              echo (' testing ......')
            }
        }

        //Stage-3 publish the artifact to nexus

        stage ('publishtonexus'){
            steps {

                nexusArtifactUploader artifacts: [[artifactId: 'javaparser-maven-sample', classifier: '', file: 'target/javaparser-maven-sample-1.2.6-SNAPSHOT.jar', type: 'jar']], credentialsId: 'c9682a36-712e-456f-89b3-5df9807c5c31', groupId: 'com.yourorganization', nexusUrl: '172.20.10.205:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'mylabdevops-snapshot', version: '1.2.6-SNAPSHOT'
            }
        }

        stage ('Deploy'){

            steps {

                echo 'deploying....'
            }
        }

        }


    }
