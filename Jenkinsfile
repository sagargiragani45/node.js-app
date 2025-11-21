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
                script {
    def app = docker.build("sagargiragani/node.js-app:${BUILD_NUMBER}")
    docker.withRegistry("https://index.docker.io/v1/", "dockerhub-cred") {
        app.push()
                    }
                }
            }
        }
    }
}
