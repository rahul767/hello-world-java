pipeline {
    agent {
        docker {
            image 'maven:3.9.6-eclipse-temurin-17'
            args '-v $HOME/.m2:/root/.m2'
        }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test Run') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
            }
        }
    }

    post {
        success {
            echo 'Build SUCCESS ✅'
        }
        failure {
            echo 'Build FAILED ❌'
        }
    }
}
