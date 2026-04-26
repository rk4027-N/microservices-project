pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'day20-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6AC26AC261F76DC0BABE63134E70D541.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'day20-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6AC26AC261F76DC0BABE63134E70D541.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
