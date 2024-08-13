pipeline {
    agent any

    stages {
        stage('Conectar a ArgoCD y listar aplicaciones') {
            steps {
                script {
                    // URL de la demo pública de ArgoCD
                    def argoCDURL = 'https://cd.apps.argoproj.io'
                    def username = 'admin'
                    def password = 'password'

                    // Primero, verificar la conexión a ArgoCD
                    bat """
                    curl -X GET -u ${username}:${password} ${argoCDURL}/api/v1/health
                    """

                    // Luego, listar las aplicaciones usando la CLI de ArgoCD
                    bat """
                    argocd app list --grpc-web -o wide --server ${argoCDURL} --username ${username} --password ${password}
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Operación exitosa"
        }
        failure {
            echo "Error en la operación"
        }
    }
}

