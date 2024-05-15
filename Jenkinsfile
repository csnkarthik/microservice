pipeline {
    agent any

    stages {
        stage('Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-token-v1', namespace: 'webapps', serverUrl: 'https://192.168.0.67:6443']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('Hello') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-token-v1', namespace: 'webapps', serverUrl: 'https://192.168.0.67:6443']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
