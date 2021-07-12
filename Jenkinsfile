#! groovy
pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS =cerdentials('global')
    }
    tools {
        gradle "gradle"
    }
    stages {
        stage('Check Gradle Version') {
            steps {
                sh 'gradle --version'
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('Build Gradle') {
            when{
                expression{
                    BRANCH_NAME == 'dev'
                }
            }
            steps {
                sh 'gradle build'
            }
        }
        stage('Build Test') {
            steps {
                echo "testing build ${SERVER_CREDENTIALS}"
            }
        }
        stage('Deploy to server') {
            steps {
                echo 'deploying build'
                withCredentials([
                        usernamePassword(credentials: 'global', usernameVariable:USER, passwordVariable:PWD)
                ]){
                    sh "some script ${USER} ${PWD}"
                }
            }
            steps{
                sshagent(['dev_server']){
                    echo 'copy file to dev server'
                    sh 'scp -o StrictHostKeyChecking=no build/libs/pipeline_scripted.jar ubuntu@192.168.50.200:/opt/sam/'
                }
            }
        }
    }
    post{
        always{
            //will be always executed
        }
        success{
            // if build succeed perform some action
        }
        failure{
            //if build failed
        }
    }
}