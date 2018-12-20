#!/usr/bin/env groovy

pipeline {
    agent any

    environment {
        NEXUS_USERNAME     = credentials('username')
        NEXUS_PASSWORD = credentials('password')
    }

    stages {
        stage('Clean build with Gradle') {
            steps {
                sh './gradlew clean'
            }
        }
        stage ('Build with Gradle') {
            steps {
                sh './gradlew build --no-daemon --info --stacktrace -PnexusUsername=NEXUS_USERNAME -PnexusPassword=NEXUS_PASSWORD'
            }
        }
        // stage ('Publish to nexus.ag04.io') {
        //     steps {
        //         sh './gradlew publish'
        //     }
        // }
    }
}
