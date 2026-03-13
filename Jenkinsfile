pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'git@github.com:mituldesai252/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mituldesai252/devops-project .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push mituldesai252/devops-project'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }

    }
}
