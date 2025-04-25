pipeline {
    agent { label 'agent1' }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/vastekruz/viernes2.git'
            }
        }
        stage('Test') {
            steps {
                // Ejecuta pytest y genera reporte JUnit
                sh 'pytest --maxfail=1 --disable-warnings -q --junitxml=results.xml'
            }
        }
    }

    post {
        always {
            // Publica el reporte en la interfaz de Jenkins
            junit 'results.xml'
        }
    }
}