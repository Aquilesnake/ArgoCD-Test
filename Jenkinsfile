pipeline {
    agent any

    stages {
        stage('Listar aplicaciones de ArgoCD') {
            steps {
                script {
                    // URL de la demo pública de ArgoCD
                    def argoCDURL = 'https://cd.apps.argoproj.io'
                    def username = 'admin'
                    def password = 'password'

                    // Listar las aplicaciones y guardar la respuesta en un archivo
                    bat """
                    curl -X GET -u ${username}:${password} ${argoCDURL}/api/v1/applications > aplicaciones.txt
                    """

                    // Mostrar el contenido del archivo de aplicaciones en la consola
                    bat 'type aplicaciones.txt'
                }
            }
        }
    }

    post {
        success {
            echo "Aplicaciones listadas exitosamente y guardadas en aplicaciones.txt"
        }
        failure {
            echo "Error al listar las aplicaciones"
        }
    }
}
