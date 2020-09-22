#!/usr/bin/env groovy
// shebang tells most editors to treat as groovy (syntax highlights, formatting, etc)

pipeline {
    agent any

    stages {
    // implicit checkout stage

        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
    }
    // post at end of stage becomes an implicit stage as well
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
