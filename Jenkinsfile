
pipeline {
    agent any

    tools {
        sonarQubeScanner 'sonar-scanner'
    }
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
   stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=devops-cicd-project \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://http://54.180.152.131:9000 \
                    -Dsonar.login=$SONAR_AUTH_TOKEN
                    '''
                }
            }
        }

    }
}
