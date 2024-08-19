pipeline {
    agent any

    stages {
        stage('Listar aplicaciones de ArgoCD en servidores') {
            steps {
                script {
                    // Parámetros de conexión (puedes cambiar las URLs después)
                    def servers = [
                        [url: 'https://cd.apps.argoproj.io', filename: 'aplicaciones_pa5.txt'],
                        [url: 'https://cd.apps.argoproj.io', filename: 'aplicaciones_ia9.txt'],
                        [url: 'https://cd.apps.argoproj.io', filename: 'aplicaciones_ia4.txt']
                    ]
                    def username = 'admin'
                    def password = 'password'

                    // Iterar sobre cada servidor y realizar la operación
                    /*servers.each { server ->
                        sh """
                        curl -X GET -u ${username}:${password} ${server.url}/api/v1/applications > ${server.filename}
                        cp ${server.filename} /ruta/a/tu/carpeta/compartida/${server.filename}
                        """
                    */
                    servers.each { server ->
                        bat """
                        curl -X GET -u ${username}:${password} ${server.url}/api/v1/applications > ${server.filename}
                        copy ${server.filename} /ruta/a/tu/carpeta/compartida/${server.filename}
                        """

                    }
                }
            }
        }
    }

    post {
        success {
            echo "Aplicaciones listadas y guardadas en la carpeta compartida en la red para todos los servidores"
        }
        failure {
            echo "Error al listar las aplicaciones o copiar los archivos"
        }
    }
}
