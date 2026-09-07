#!/usr/bin/env groovy

library identifier: 'jenkins-shared-library@main', retriever: modernSCM(
        [$class: 'GitSCMSource',
        remote: 'https://gitlab.com/twn-devops-bootcamp/latest/08-jenkins/jenkins-shared-library.git',
        credentialsId: 'gitlab-credentials'])

def gv


pipeline {
    agent any
    tools {
        maven 'maven-3.9'
    }
    stages{
        stage("init"){
            steps{
                script{
                   gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    buildJar()
                }
            }
        }

        stage("build and push image") {
            steps {
                script {
                    buildImage 'jadyamorim/jadydevops:jma-3.0'
                    dockerLogin()
                    dockerPush 'jadyamorim/jadydevops:jma-3.0'
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                     echo "deploying the application..."
                }
            }
        }
    }
}
