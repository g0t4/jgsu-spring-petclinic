pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        stage('Checkout'){
            steps {
                git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                shell('Hey, Im here')
                sh './mvnw clean package'
                // sh 'true'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
                changed {
                    emailext subject: "Job \'${JOB_NAME}\' (${BUILD_NUMBER}) ${currentBuild.result}",
                        body: "Please go to ${BUILD_URL} and verify the build",
                        attachLog: true,
                        compressLog: true,
                        to: "johallengineer@gmail.com",
                        recipientProviders: [upstreamDevelopers(), requestor()]
                }
            }

        }
    }
}
