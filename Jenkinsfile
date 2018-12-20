#!/usr/bin/env groovy

pipeline {

    environment {
        def git_creds = 'c652d29e-f9f8-4008-b81e-5e582bb4f4d3' 
    }

    agent any

    stages {
        stage('Clean build with Gradle') {
            steps {
                sh './gradlew clean'
            }
        }
        stage ('Build with Gradle') {
            steps {
                withCredentials([usernamePassword(credentialsId: ${git_creds}, usernameVariable: 'NEXUS_USERNAME', passwordVariable: 'NEXUS_PASSWORD')]) {
                    sh "./gradlew build --no-daemon --info --stacktrace -PnexusUsername=${env.NEXUS_USERNAME} -PnexusPassword=${env.NEXUS_PASSWORD}"
                }
            }
        }
        stage ('Publish to nexus.ag04.io') {
             steps {
                 sh './gradlew publish'
             }
         }
    }
}
