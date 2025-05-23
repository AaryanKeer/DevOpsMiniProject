pipeline {
    agent any

    environment {
        TOMCAT_HOME = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 10.1'
        APP_NAME = 'cyborgsite'
        CONTAINER_NAME = 'cyborgweb'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat "docker build -t %APP_NAME% ."
            }
        }

        stage('Remove Previous Container') {
            steps {
                // Stop and remove container if it exists
                bat 'docker rm -f %CONTAINER_NAME% || exit 0'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat "docker run -d -p 8080:80 --name %CONTAINER_NAME% %APP_NAME%"
            }
        }
    }

    post {
        success {
            echo '✅ Site deployed successfully! Visit: http://localhost:8080'
        }
        failure {
            echo '❌ Deployment failed.'
        }
    }
}
