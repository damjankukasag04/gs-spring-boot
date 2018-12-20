#!/usr/bin/env groovy

pipeline {

    environment {
        def nexus_creds = 'nexus_creds' 
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
                withCredentials([usernamePassword(credentialsId: ${nexus_creds}, usernameVariable: 'NEXUS_USERNAME', passwordVariable: 'NEXUS_PASSWORD')]) {
                    sh "./gradlew build --no-daemon --info --stacktrace -PNEXUSUSERNAME=${env.NEXUS_USERNAME} -PNEXUSPASSWORD=${env.NEXUS_PASSWORD}"
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
