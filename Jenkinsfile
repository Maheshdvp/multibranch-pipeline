pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t mahesh663/abinay:bus .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push mahesh663/abinay:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus -p 8888:80 mahesh663/abinay:bus'
            }
        }
    }
}
