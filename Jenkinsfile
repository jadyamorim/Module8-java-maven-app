#!/user/bin/env groovy

@Library('jenkins-shared-library')_
def gv


pipeline {
    agent any
    tools {
        maven 'Maven'
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

        stage("build image") {
            steps {
                script {
                    buildImage 'jadyamorim/jadydevops:jma-3.0'
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
