pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/mituldesai252/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
            sh 'docker build -t mitul11111/devops-project .'
            }
        }

        stage('Push Image'){
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
            sh 'echo $PASS | docker login -u $USER --password-stdin'
            sh 'docker push mitul11111/devops-project'
        }
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
