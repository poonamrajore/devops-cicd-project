
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
 
       stage('SonarQube Scan') {
    steps {
        withSonarQubeEnv('SonarQube') {
            sh '''
            /opt/sonar-scanner/bin/sonar-scanner \
            -Dsonar.projectKey=devops-cicd-project \
            -Dsonar.sources=. \
            -Dsonar.host.url=http://54.180.152.131:9000
            '''

                }
            }
        }
     
     stage('Build Docker Image') {
    steps {
        echo "Building Docker Image"
        sh 'docker build -t devops-cicd-app .'
         }
       }
stage('Push Docker Image') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
            sh '''
            docker login -u $DOCKER_USER -p $DOCKER_PASS
            docker tag devops-cicd-app $DOCKER_USER/devops-cicd-app:latest
            docker push $DOCKER_USER/devops-cicd-app:latest
            '''
        }
    }
  }

 }
}
