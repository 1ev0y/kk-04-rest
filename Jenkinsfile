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
        JAVA_HOME = '/usr/lib/jvm/java-21-amazon-corretto.x86_64'
        PATH = "${JAVA_HOME}/bin:${PATH}"
    }
    steps{
            echo 'Java Version'
            sh 'java -version'
            echo 'Javac Version'
            sh 'javac -version'
            echo 'Maven Version'
            sh 'mvn -version'
            echo 'JAVA_HOME'
            sh 'echo $JAVA_HOME'
            echo 'PATH'
            sh 'echo $PATH'
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