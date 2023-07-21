pipeline {
    agent any

    environment {
        dockerhubCredentials = 'dockerhub-credentials'
        dockerImageTag = "salman1091/my-web-app:${BUILD_TAG.toLowerCase()}"
        dockerUsername = credentials('dockerhub-credentials').USUARIO
        dockerPassword = credentials('dockerhub-credentials').SENHA
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh "docker build -t $dockerImageTag ."
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker login -u $dockerUsername -p $dockerPassword"
                sh "docker push $dockerImageTag"
            }
        }
    }
}
