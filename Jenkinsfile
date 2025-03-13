pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://7ED72CA368D7B00A3E931B05FED13AC4.yl4.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
               }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8-token', namespace: 'webapps', serverUrl: 'https://7ED72CA368D7B00A3E931B05FED13AC4.yl4.ap-south-1.eks.amazonaws.com']]) {
                 sh " kubectl get svc -n webapps"
               }
                
            }
        }
    }
}
