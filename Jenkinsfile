pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
              withKubeConfig(caCertificate: '', clusterName: 'EKS-micro', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://595CF5243710C2D1E32480290970C6C0.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl appy -f deployment-service.yml"
                    sleep 60
                }  
            }
        }
        stage('verify deloymentsp') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-micro', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://595CF5243710C2D1E32480290970C6C0.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
