pipeline { 
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://33DDD801C073F539C20D022BD53CBA08.sk1.ap-south-1.eks.amazonaws.com']]) {
                   sh" kubectl apply -f deployment-service.yml"
                
                }
                   
            }
        }
    
        
        stage('verify Deployment ') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://33DDD801C073F539C20D022BD53CBA08.sk1.ap-south-1.eks.amazonaws.com']]) {
                   sh " kubectl get svc -n webapps"
                }
            }
        }
    }
}
