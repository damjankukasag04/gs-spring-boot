#!/usr/bin/env groovy

pipeline {

    // environment {
    //     def nexus_creds = '822b18eb-56d3-4121-b39d-3db31ffefe8a' 
    // }

    agent any

    stages {
        stage('Clean build with Gradle') {
            steps {
                sh './gradlew clean'
            }
        }
        stage('Dummy build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage ('Build with Gradle') {
            steps {
                // withCredentials([usernamePassword(credentialsId: '822b18eb-56d3-4121-b39d-3db31ffefe8a', usernameVariable: 'NEXUS_USERNAME', passwordVariable: 'NEXUS_PASSWORD')]) {
                    // sh "./gradlew build --no-daemon --info --stacktrace -PNEXUSUSERNAME=$NEXUS_USERNAME -PNEXUSPASSWORD=$NEXUS_PASSWORD"
                sh "./gradlew build --no-daemon --info --stacktrace"
                // }
            }
        }
        // stage ('Publish to nexus.ag04.io') {
        //     steps {
        //         sh './gradlew publish'
        //     }
        // }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }        
}
