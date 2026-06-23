@Library('my-gradle-library') _

pipeline {
    agent any
    tools {
        jdk 'jdk17'
    }
    stages {
        stage('Compile & Build') {
            steps {
                sh 'chmod +x gradlew'
        
                sh './gradlew compileJava'
            }
        }
        
        // Di sinilah optimasi paralel terjadi
        stage('Parallel Tests & Analysis') {
            parallel {
                stage('Unit Testing') {
                    steps {
                        sh './gradlew test'
                    }
                }
                stage('Static Code Analysis') {
                    steps {
                        // Contoh jika menggunakan Checkstyle / SonarQube / PMD
                        echo "Menjalankan analisis kualitas kode..."
                        // sh './gradlew checkstyleMain'
                    }
                }
            }
        }
    }
}