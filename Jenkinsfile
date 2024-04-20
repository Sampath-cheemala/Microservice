pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://72EEC4DB8B36442BE91EB14C9F3401CA.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 30
                }    
               
            }
        }
        stage('verify deployments') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://72EEC4DB8B36442BE91EB14C9F3401CA.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh  "kubectl get all -n webapps"
                }
            }
        }
    }
}
