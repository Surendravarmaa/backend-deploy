pipeline {
    agent {
        label 'AGENT-1'
    }
    parameters {
        string(name: 'appVersion', defaultValue: '1.0.0', description: 'What is the application version?')
    }
    environment{
        def appVersion = '' //variable declaration
        nexusUrl = 'nexus.surendra.online:8081'
    } 
    stages {
        stage('read the version') {
            steps {
                script {
                    echo "Application version: ${params.appVersion}"
                }
            }
        }
        stage('Init') {
            steps {
                sh """
                    cd terraform
                    terraform init
                """
            }
        }
        stage('Plan') {
            steps {
                sh """
                    cd terraform
                    terraform plan -var="app_version=${params.appVersion}"
                """
            }
        }
        // stage('Deploy') {
        //     steps {
        //         sh """
        //             cd terraform
        //             terraform appl
        //         """
        //     }
        // }
    }
    post {
        always {
            echo 'I will always say Hello again'
            deleteDir()
        }
        success {
            echo 'I will run when pipeline is success'
        }
        failure {
            echo 'I will run when pipeline is failure'
        }
    }
}

