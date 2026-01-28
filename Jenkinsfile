pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/deekshithabasavaraju/simple-java-project.git'
            }
        }

        stages {

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
        
