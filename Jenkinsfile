pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://03D2D22A64F3AA6A361860CA1843BC4D.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://03D2D22A64F3AA6A361860CA1843BC4D.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
