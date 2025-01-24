pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials:[[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'kubertoken', namespace: 'webapps', serverUrl: 'https://B7BCF84FC956EDF421EE84B39512FC57.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials:[[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'kubertoken', namespace: 'webapps', serverUrl: 'https://B7BCF84FC956EDF421EE84B39512FC57.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
