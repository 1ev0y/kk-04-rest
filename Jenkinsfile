pipeline {
    agent any
    stages {
    stage('checkout') {
        steps{
            git branch: 'main',
            url: 'https://github.com/neueda-learning/kk-04-rest.git'
        }
    }
    stage ('Environment'){
    environment {
        JAVA_HOME = '/usr/lib/jvm/java-21-amazon-corretto.x86_64/bin/java'
        PATH = "${JAVA_HOME}/bin:${PATH}"
    }
    steps{
            sh 'java -version'
            sh 'javac -version'
            sh 'mvn -version'
            sh 'echo $JAVA_HOME'
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