#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage('Clean build with Gradle') {
            steps {
                sh './gradlew clean'
            }
        }
        stage ('Build with Gradle') {
            steps {
                sh './gradlew build --no-daemon --info --stacktrace'
            }
        }
        stage ('Publish to nexus.ag04.io') {
            steps {
                sh './gradlew publish'
            }
        }
    }
}
