pipeline {
    agent any

    environment {
        // Path to kubectl configuration file
        KUBECONFIG = '~/.kube/config' 
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Pull the latest files from GitHub
                git branch: 'main', url: 'https://github.com/HarshavardhanVadla/EKS-Jenkins.git'
            }
        }
        
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Apply Kubernetes deployment and service files
                    sh 'kubectl apply -f httpd-deployment.yaml'
                    sh 'kubectl apply -f httpd-service.yaml'
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
