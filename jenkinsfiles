pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://0B1C9595A0345D46A0574A39E9B3B6A0.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl apply -f deployment-service.yml' // our main branch file
                } 
            }
        }

        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://0B1C9595A0345D46A0574A39E9B3B6A0.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl get svc -n webapps'
                } 
            }
        }
    }
}
