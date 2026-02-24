pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'Eks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5CEB21CCF058E6739A4E4C24D8575984.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'Eks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5CEB21CCF058E6739A4E4C24D8575984.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
