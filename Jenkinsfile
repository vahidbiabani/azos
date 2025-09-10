pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vahidbiabani/azos.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t azos .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                   docker rm -f azos || true
                   docker run -d -p 3000:3000 --name azos azos
                '''
            }
        }
    }
}
