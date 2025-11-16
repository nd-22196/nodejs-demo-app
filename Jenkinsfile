pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/nd-22196/nodejs-demo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("snd3226/nodejs-demo-app:latest")
                }
            }
        }

        stage('Run Tests') {
            steps {
                echo "Running tests..."
                // Example: sh 'npm test'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-creds') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
