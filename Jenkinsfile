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
     curl -X GET -u ${username}:${password} ${argoCDURL}/api/v1/health > respuesta.txt 2>&1
     """
    }
   }
  }
 }

 post {
  success {
   // Acciones al éxito
   echo "Conexión a ArgoCD exitosa"
   sh 'cat respuesta.txt'
  }
  failure {
   // Acciones al fallo
   echo "Error al conectar a ArgoCD"
   sh 'cat respuesta.txt'
  }
 }
}
