pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://15D9D3CEC874396BB6902E3E1B824E70.gr7.ap-south-1.eks.amazonaws.com']]) {
                 sh "kubectl apply -f deployment-service.yml"
               } 
            }
        }
        
        stage('verify deployment') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://15D9D3CEC874396BB6902E3E1B824E70.gr7.ap-south-1.eks.amazonaws.com']]) {
                 sh "kubectl get svc -n webapps"
               }  
            }
        }
    }
}
