pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t dockopswebsite .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker container...'
                sh 'docker stop dockops-container || true'
                sh 'docker rm dockops-container || true'
                sh 'docker run -d -p 8080:80 --name dockops-container dockopswebsite'
            }
        }
    }
}
