pipeline {
    agent any

    stages {
        stage ('Clean Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean'
                }
            }
        }

        stage ('Build Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn compile'
                }
            }
        }


        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }

        stage ('package Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn package'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                nexusArtifactUploader artifacts: 
                    [
                        [
                            artifactId: 'jenkins-example', 
                            classifier: '', 
                            file: 'target/jenkins-example-1.0-SNAPSHOT.jar', 
                            type: 'jar']], 
                    credentialsId: 'nexusdemo', 
                    groupId: 'com.techprimers.testing', 
                    nexusUrl: 'ec2-18-192-245-57.eu-central-1.compute.amazonaws.com:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'simpleapp-nexusdemo-pavol', 
                    version: '1.0-SNAPSHOT'
                }
            }
        }
    }

