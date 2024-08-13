pipeline {
    agent any

    stages {
        stage('Conectar a ArgoCD') {
            steps {
                script {
                    def argoCDURL = 'http://localhost:8080'
                    def username = 'tu_usuario'
                    def password = 'tu_contraseña'

                    // Utilizando cmd /C
                    sh """
                    cmd /C "curl -X GET -u ${username}:${password} ${argoCDURL}/api/v1/health > respuesta.txt 2>&1"
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
