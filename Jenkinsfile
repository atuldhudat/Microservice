pipeline {
    agent any

    stages {
        stage('deploy to k8s') {
            steps {
                withKubeConfig(caCertificate: '', 
                              clusterName: 'EKS-1', 
                              contextName: '', 
                              credentialsId: 'k8s-token', 
                              namespace: 'webapps', 
                              restrictKubeConfigAccess: false, 
                              serverUrl: 'https://C57D53AA4EDB2CBB231433D9ED7CF56D.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', 
                              clusterName: 'EKS-1', 
                              contextName: '', 
                              credentialsId: 'k8s-token', 
                              namespace: 'webapps', 
                              restrictKubeConfigAccess: false, 
                              serverUrl: 'https://C57D53AA4EDB2CBB231433D9ED7CF56D.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
