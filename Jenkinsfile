pipeline {
    agent any
    environment {
        IMAGE_NAME = "abhi887133/nginx-demo"
    }
    stages {
        stage('Git Checkout') {
            steps {
                // Replace with your actual GitHub repository URL
               #  git 'https://github.com/YOUR_USER/my-devops-app.git'
                git   'https://github.com/Abhi887133/my-devops-app.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$BUILD_NUMBER .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withCredentials([
                  usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'abhi887133',
                    passwordVariable: 'Ab8871339517'
                  )
                ]) {
                    sh '''
                    echo "$PASS" | docker login -u "$USER" --password-stdin
                    docker push $IMAGE_NAME:$BUILD_NUMBER
                    '''
                }
            }
        }
    }
}
