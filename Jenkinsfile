pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Atharv1906/gradle-demo.git'
            }
        }
        
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        
        stage('Test') {
            steps {
                sh './gradlew test'
            }
            post {
                always {
                    junit 'build/test-results/test/*.xml'
                }
            }
        }
        
        stage('Package') {
            steps {
                sh './gradlew assemble'
            }
        }
    }
    
    post {
        success {
            echo 'Gradle Build Successful ✅'
        }
        failure {
            echo 'Gradle Build Failed ❌'
        }
    }
}
