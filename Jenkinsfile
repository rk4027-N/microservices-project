pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'day20-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://84820C3AD9801E4E8B7572783CFEF4CE.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'day20-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://84820C3AD9801E4E8B7572783CFEF4CE.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
