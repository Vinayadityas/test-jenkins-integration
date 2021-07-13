#! groovy
pipeline {
    agent any

    tools {
        gradle "gradle"
    }
    stages {
        stage('Check Gradle Version') {
            steps {
                sh 'gradle --version'

            }
        }
        stage('Build Gradle') {
            steps {
                sh 'gradle build'
            }
        }


        stage('Copy to dev server'){
            steps{
                steps{
                    echo 'copy file to dev server'
                    sshagent(['dev_server']){

                        sh 'scp build/libs/pipeline_scripted.jar ubuntu@192.168.50.200:/opt/sam/'
                    }
                }
            }
        }
    }
}