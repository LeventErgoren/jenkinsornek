pipeline {
    agent any

    tools {
        // Jenkins'te tanımlı olan Maven ve JDK isimleri
        // Eğer isimlerin farklıysa buraları güncellemeyi unutma
        maven 'Maven-3' 
        jdk 'Java-17'
    }

    stages {
        stage('Checkout') {
            steps {
                // Arayüzde "Branches to build" kısmında ne seçtiysen (boş veya *)
                // Jenkins o branch'in kodunu burada çeker.
                checkout scm
            }
        }

        stage('Test (JUnit)') {
            steps {
                script {
                    echo 'Maven testleri başlatılıyor...'
                    // Test başarısız olursa (URL erişilemezse) pipeline burada patlar ve durur.
                    sh 'mvn clean test'
                }
            }
        }

        stage('Deploy') {
            // Sadece önceki test aşaması başarılı olursa burası çalışır
            steps {
                script {
                    echo '--------------------------------------------'
                    echo 'Test Başarılı! Deploy adımı çalışıyor...'
                    echo 'Deploy işlemi başarıyla tamamlandı.'
                    echo '--------------------------------------------'
                }
            }
        }
    }

    post {
        failure {
            echo 'HATA: Pipeline başarısız oldu. Test geçemedi.'
        }
    }
}