pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
        PROJECT_DIR = '/var/www/mi-proyecto'
    }

    triggers {
        githubPush() // se activa al push o al merge del PR
    }

    stages {
        stage('Actualizar código') {
            steps {
                dir("${env.PROJECT_DIR}") {
                    // Asegura que estás en la última versión
                    sh 'git pull origin main'
                }
            }
        }

        stage('Instalar dependencias') {
            steps {
                dir("${env.PROJECT_DIR}") {
                    sh 'npm install --production'
                }
            }
        }

        stage('Reiniciar servidor web') {
            steps {
                dir("${env.PROJECT_DIR}") {
                    // Si usas PM2:
                    // sh 'pm2 restart mi-proyecto || pm2 start app.js --name mi-proyecto'
                    
                    // O si usas systemctl:
                    sh 'sudo systemctl restart mi-proyecto'

                    // O Docker Compose:
                    // sh 'docker-compose down && docker-compose up -d'
                }
            }
        }
    }

    post {
        failure {
            echo "❌ La construcción falló."
        }
        success {
            echo "✅ Despliegue completo."
        }
    }
}
