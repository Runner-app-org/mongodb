pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Pulls the API Gateway repository from GitHub
                git url: 'https://github.com/Runner-app-org/mongodb.git', branch: 'master'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                withAWS(credentials: 'aws-credentials-id', region: 'ap-southeast-1') {
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}