pipeline {
    agent any

   // tools {
   //     // Install the Maven version configured as "M3" and add it to the path.
    //    maven "M3"
   // }

    stages {
         stage('Checkout') {
            steps {
                git url :'https://github.com/fhabumugisha/jgsu-spring-petclinic.git', branch :'main'

            }

        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }

            post {
           //     // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
