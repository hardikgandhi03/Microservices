pipeline {
    agent any

stages {
        stage('Deploy to Kubernetes!') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Cluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://39227DDDB8A083224E373290C4FD41FC.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                sleep 60
                }
            }
        }
    
    
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Cluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://39227DDDB8A083224E373290C4FD41FC.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
