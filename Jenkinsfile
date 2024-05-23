pipeline { 
    agent slave

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh 'pwd'
                        sh '$USER'
                        sh "sudo docker build -t csnkarthik/shippingservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {

                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "sudo docker push csnkarthik/shippingservice:latest "
                    }
                }
            }
        }
    }
}
