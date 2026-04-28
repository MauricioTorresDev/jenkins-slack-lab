pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Notificación de inicio
                slackSend(color: '#FFFF00', message: "🚀 Iniciando Pipeline: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}")
                
                echo 'Construyendo el proyecto...'
                bat 'echo "Construyendo..."'
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
                // Simula un error cambiando '0' por '1' si quieres probar la notificación de falla
                bat 'exit 0' 
            }
        }
    }

    post {
        success {
            slackSend(color: 'good', message: "✅ ¡Éxito! El proyecto ${env.JOB_NAME} se completó correctamente. \nResultado: ${currentBuild.currentResult} \nFecha: ${new Date().format('dd-MM-yyyy HH:mm')}")
        }
        failure {
            slackSend(color: 'danger', message: "❌ ¡Error! El pipeline de ${env.JOB_NAME} falló. \nRevisar: ${env.BUILD_URL}")
        }
    }
}
