
pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '',
                    clusterName: 'EKS-2',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://37670BD29B69088CC7FA7126CE9EE812.gr7.ap-southeast-2.eks.amazonaws.com'
                ]]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }

        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '',
                    clusterName: 'EKS-2',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://37670BD29B69088CC7FA7126CE9EE812.gr7.ap-southeast-2.eks.amazonaws.com'
                ]]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
