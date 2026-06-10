pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Code downloaded from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nginx-demo .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f nginx-demo || true
                docker run -d -p 8081:80 --name nginx-demo nginx-demo
                '''
            }
        }
    }
}
