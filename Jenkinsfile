pipeline {
    agent any

    stages {
        stage('Conectar a ArgoCD') {
            steps {
                script {
                    // URL de la demo pública de ArgoCD
                    def argoCDURL = 'https://cd.apps.argoproj.io'
                    // Las credenciales predeterminadas de la demo pública
                    def username = 'admin'
                    def password = 'password'

                    // Ejecutando la petición HTTP para verificar la conexión usando bat
                    bat """
                    curl -X GET -u ${username}:${password} ${argoCDURL}/api/v1/health
                    """
                }
            }
        }
    }

    post {
        success {
            // Acciones al éxito
            echo "Conexión a ArgoCD exitosa"
        }
        failure {
            // Acciones al fallo
            echo "Error al conectar a ArgoCD"
        }
    }
}
