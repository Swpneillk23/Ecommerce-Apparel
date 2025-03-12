pipeline { 
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://DAAE472C545B413788954BBACD54CB39.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                }
                   
            }
    }
    
        stage('verify Deployment ') {
            steps {
                wwithKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://DAAE472C545B413788954BBACD54CB39.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get svc -n webapps" 
                }
            }
        }
    }

}
