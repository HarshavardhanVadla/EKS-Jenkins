pipeline {
    agent any

    environment {
        KUBECONFIG = '~/.kube/config' // Ensure this path is correct
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/HarshavardhanVadla/EKS-Jenkins.git'
            }
        }
        
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Apply Kubernetes deployment and service files
                    sh 'kubectl apply -f httpd-deployment.yaml --validate=false'
                    sh 'kubectl apply -f httpd-service.yaml --validate=false'
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
