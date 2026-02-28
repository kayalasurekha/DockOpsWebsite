pipeline {
    agent any

    stages {

        stage('Checkout SCM') {
            steps {
                echo 'Checking out source code...'
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
                echo 'Stopping old container if exists...'
                sh 'docker stop dockops-container || true'
                sh 'docker rm dockops-container || true'

                echo 'Running new container on port 8082...'
                sh 'docker run -d -p 8082:80 --name dockops-container dockopswebsite'
            }
        }
    }
}
