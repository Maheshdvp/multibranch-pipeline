pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                sh 'docker build -t mahesh663/abinay:train .'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push mahesh663/abinay:train'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name train -p 9999:80 mahesh663/abinay:train'
            }
        }
    }
}
