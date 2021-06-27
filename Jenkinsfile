pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    stages {
//         stage('Git Checkout') {
//             steps {
//                 // Get some code from a GitHub repository
//                git branch: 'main', url: 'https://github.com/Fayez74/jgsu-spring-petclinic.git'
//             }
//         }
        stage('Build') {
            input {
                message 'Build Now?'
                ok 'Approve'
            }
            steps {
                // Run Maven on a Unix agent.
                sh "./mvnw clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                always {
                    junit 'target/surefire-reports/*.xml'
                    archiveArtifacts 'target/*.jar'
                } 
            }
        }
    }
}
