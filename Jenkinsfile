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

     // Ejecutando la petición HTTP para verificar la conexión
     sh """
     curl -X GET -u ${username}:${password} ${argoCDURL}/api/v1/health
     """
     // Nota: Si la conexión es exitosa, curl devolverá el contenido del endpoint.
     // No estamos redirigiendo la salida a un archivo para simplificar.
    }
   }
  }
 }

 post {
  success {
   // Acciones al éxito
   echo "Conexión a ArgoCD exitosa"
   // Comentamos la siguiente línea porque no estamos generando 'respuesta.txt'
   // sh 'cat respuesta.txt'
  }
  failure {
   // Acciones al fallo
   echo "Error al conectar a ArgoCD"
   // Comentamos la siguiente línea porque no estamos generando 'respuesta.txt'
   // sh 'cat respuesta.txt'
  }
 }
}
