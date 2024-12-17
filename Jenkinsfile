
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t shaikmustafa/service:v1 .'
            }
        }
        stage('Push'){
            steps{
                script{
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker push shaikmustafa/service:v1'
                    }
                }
            }
        }
    }
}
