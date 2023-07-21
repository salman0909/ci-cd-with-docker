pipeline {
    agent any

    environment {
        dockerhubCredentials = 'dockerhub-credentials'
        dockerImageTag = "Salman1091/ci-cd-with-docker:${BUILD_ID}"
        dockerUsername = credentials('dockerhub-credentials')
        dockerPassword = credentials('dockerhub-credentials')
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


