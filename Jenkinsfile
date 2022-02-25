#!/usr/bin/env groovy

pipeline {
    agent any
    triggers {
        pollSCM ('* * * * *')
    }
    stages {
        
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
       
    }
     post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                    //}
                //changed 
                    emailext subject: "Job \'${JOB_NAME}\' (${BUILD_NUMBER}) ${currentBuild.result}",
                        body: "Please go to ${BUILD_URL} and verify the build", 
                        attachLog:true, 
                        compressLog: true, 
                        to : "fabriceboris@yahoo.fr",
                        recipientProviders: [upstreamDevelopers(), developers()]
                        
                }
            }
}
