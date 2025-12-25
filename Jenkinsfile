pipeline {
    agent any
    stages {
        stage('Build & Test') {
            steps {
                // Windows için bat ve mvnw.cmd
                bat 'mvnw.cmd clean test'
            }
        }

        stage('Deploy') {
            steps {
                // Sadece test başarılıysa buraya girer
                echo 'Deploy aşaması...'
            }
        }
    }
    post {
        success {
            echo 'Başarılı'
        }
        failure {
            echo 'Başarısız'
        }
    }
}
