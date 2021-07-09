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
        stage('Build Test') {
            steps {
                echo 'testing build'
            }
        }
    }
}