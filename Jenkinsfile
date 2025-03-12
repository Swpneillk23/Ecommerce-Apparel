pipeline {
    agent any

    stages {
        stage('Deploy to Kuberbenetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://41B608D5B49FA59A5D1AEE8D55984EE5.gr7.ap-south-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
                 }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://41B608D5B49FA59A5D1AEE8D55984EE5.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
