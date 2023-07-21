pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("ci-cd-with-docker:${env.BUILD_ID}")
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-credentials') {
                        docker.image("ci-cd-with-docker:${env.BUILD_ID}").push()
                    }
                }
            }
        }
    }
}
