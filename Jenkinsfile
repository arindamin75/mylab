pipeline{

    agent any
    tools{

        maven 'maven'
    }

    environment {

        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()

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
              script{  

                def NexusRepo = Version.endsWith("SNAPSHOT") ? "mylabdevops-snapshot" : "mylabdevops-release"   
                nexusArtifactUploader artifacts: 
                [[artifactId: '${ArtifactId}', 
                classifier: '', 
                file: 'target/javaparser-maven-sample-1.2.6-SNAPSHOT.jar', 
                type: 'jar']], 
                credentialsId: 'e1203114-e235-4d68-a1cb-cbaa12f43233', 
                groupId: '${GroupId}', 
                nexusUrl: '172.20.10.205:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: '${NexusRepo}', 
                version: '1.2.6-SNAPSHOT'
              }
            }
        }
        // Stage 4 : Print some information
        stage ('Print Environment variables'){
            steps {
                        echo "Artifact ID is '${ArtifactId}'"
                        echo "Version is '${Version}'"
                        echo "GroupID is '${GroupId}'"
                        echo "Name is '${Name}'"
                    }
                }

        stage ('Deploy'){

            steps {

                echo 'deploying....'
            }
        }

        }


    }
