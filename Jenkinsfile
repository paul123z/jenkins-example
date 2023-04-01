/* // chat gpt sugest
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'nexusdemo', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASSWORD')]) {
                    sh 'mvn deploy -Dmaven.test.skip=true -DaltDeploymentRepository=pavol-mvn-deploy::default::http://ec2-3-68-90-3.eu-central-1.compute.amazonaws.com:8081/repository/pavol-mvn-deploy/ -Dusername=$NEXUS_USER -Dpassword=$NEXUS_PASSWORD'
                }
            }
        }
    }
*/





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

/*
        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }
*/
        stage ('package Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn package'
                }
            }
        }


        stage ('deploy Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                
                    withCredentials([usernamePassword(credentialsId: 'nexusdemo', passwordVariable: 'nexuspw', usernameVariable: 'nexus')]) {
    sh 'mvn deploy -Dmaven.test.skip=true -DaltDeploymentRepository=pavol-mvn-deploy::default::http://ec2-3-68-90-3.eu-central-1.compute.amazonaws.com:8081/repository/pavol-mvn-deploy/ -Dusername=$nexus -Dpassword=$nexuspw'
}
                }
                    
              
            }
        }
        }
    }

