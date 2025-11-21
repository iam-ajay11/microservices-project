pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-ajay1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F43FC07C3FD32271C54AD2EE9E3C4B8C.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-ajay1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F43FC07C3FD32271C54AD2EE9E3C4B8C.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
