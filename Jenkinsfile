pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cyborgsite .'
            }
        }
        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 8080:80 --name cyborgweb cyborgsite'
            }
        }
    }
}
