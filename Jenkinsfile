pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t mahesh663/abinay:bank .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push mahesh663/abinay:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank2 -p 4455:80 mahesh663/abinay:bank'
            }
        }
    }
}
