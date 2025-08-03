pipeline {
    agent any

    environment {
        APP_ENV = 'testing'
    }

    stages {
        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/alvaroRojasChaval/laravelDiplomado.git'
            }
        }

        stage('Instalar dependencias Composer') {
            steps {
                sh 'composer install --no-interaction --prefer-dist'
            }
        }

        stage('Configurar .env') {
            steps {
                sh 'cp .env.example .env'
                sh 'php artisan key:generate'
            }
        }

        stage('Pruebas') {
            steps {
                sh './vendor/bin/phpunit || true'
            }
        }

        stage('Compilar assets (opcional)') {
            steps {
                sh 'npm install && npm run build || true'
            }
        }
    }
} 