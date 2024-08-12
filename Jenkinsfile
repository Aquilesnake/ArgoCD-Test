pipeline {
    agent any

    stages {
        stage('Connect to ArgoCD') {
            steps {
                sh 'argocd login 192.168.1.100:8090 --sso'
                sh 'argocd app list --grpc-web -o wide'
            }
        }
    }
}
