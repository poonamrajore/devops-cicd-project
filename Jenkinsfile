pipeline {
    agent any

    stages {

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
