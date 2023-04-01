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


        stage ('package Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }
        }
    }

