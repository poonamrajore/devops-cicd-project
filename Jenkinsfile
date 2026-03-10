pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo "Pulling code from GitHub"
                git 'https://github.com/poonamrajore/devops-cicd-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing packages"
                sh 'npm install'
            }
        }

        stage('Build Test') {
            steps {
                echo "Testing application"
                sh 'node -v'
            }
        }

    }
}
