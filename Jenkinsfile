pipeline {
    agent any

    stages {
        stage('Connect To GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Kaydollar/my-pipeline-job.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-html-image .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker rm -f my-html-container || true'
                    // Run new container
                    sh 'docker run -d -p 8081:80 --name my-html-container my-html-image'
                }
            }
        }
    }
}

