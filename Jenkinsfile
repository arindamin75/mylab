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
            step {

              echo (' testing ......')
            }
        }

        stage ('Deploy'){

            steps {

                echo 'deploying....'
            }
        }

        }


    }
