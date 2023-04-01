pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean compile'
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
                    nexusUrl: 'ec2-3-68-90-3.eu-central-1.compute.amazonaws.com:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://ec2-3-68-90-3.eu-central-1.compute.amazonaws.com:8081/repository/simpleapp-nexusdemo-pavol/', 
                    version: '1.0-SNAPSHOT'
                }
            }
        }
    }
}
