pipeline {
    agent any

    stages {

        stage('Build App') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                    docker rm -f devops-container || true
                    docker run -d -p 8080:8080 --name devops-container devops-app
                '''
            }
        }
    }
}
