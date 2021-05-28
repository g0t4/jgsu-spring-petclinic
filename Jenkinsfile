pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        stage('Checkout'){
            steps {
                parallel masterBranch: {
                git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
                }, devBranch: {
                git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'dev'
                },
                failFast: true //|false
                }
            }
        //Added this lines to create dev branch on remote
        // stage('Checkout'){
        //     steps {
        //         git url: 'https://github.com/johannesanchez/jgsu-spring-petclinic', branch: 'main'
        //     }
        // }
    }
}
