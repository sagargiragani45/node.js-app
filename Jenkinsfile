pipeline {
    agent any
    environment {
        IMAGE = "sagargiragani/node.js-app:${BUILD_NUMBER}"

    }
    stages {
        stage('clone code') {
            steps {
                git branch: 'master',
                url: 'https://github.com/sagargiragani45/node.js-app.git'
            }
        }
        stage('Insatll Dependencies') {
            steps {
                sh 'npm install'

            }
        }
        stage('Docker Build') {
            steps {
                script {
                    app = docker.build("${IMAGE}")
                }
            }
        }
        stage('Docker Push'){
            steps {
                docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-cred') {
                    
                    app.push()
                }
            }
        }
    }
}
