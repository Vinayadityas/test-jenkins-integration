#!/usr/bin/env groovy
node{
    stage('Build'){
        echo "Building the project"
        sh './gradlew clean build'
    }
    stage('Test'){
        echo "testing the project"
    }
    stage('Deploy'){
        echo "deploying the project"
    }
}