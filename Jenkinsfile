pipeline {
    agent any
    stages {
    stage('checkout') {
        steps{
            git branch: 'main',
            url: 'https://github.com/neueda-learning/kk-04-rest.git'
        }
    }
    stage('Build') {
        steps {
            echo 'building...'
            // Add test steps here
            sh 'mvn clean package -DskipTests'
        }
    }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add deploy steps here
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }
    }
}