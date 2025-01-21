pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials:[[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'kubertoken', namespace: 'webapps', serverUrl: 'https://3A7053EB2D754BF8B9B93D81C49D5EBC.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials:[[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'kubertoken', namespace: 'webapps', serverUrl: 'https://3A7053EB2D754BF8B9B93D81C49D5EBC.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
