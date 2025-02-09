pipeline {
    agent any
    environment {
        PYTHON = "/usr/bin/python3"
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/Ferocious71/CI-CD-Pipeline-using-Jenkins-Gihub-Actions-and-flask-application.git'
            }
        }
        stage('Build') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                bat 'pytest tests/'
            }
        }
        stage('Deploy') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                bat 'nohup python3 app.py &'
            }
        }
    }
    post {
        success {
            mail to: 'salmanmuneeb@gmail.com',
                 subject: "Jenkins Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "The build was successful!"
        }
        failure {
            mail to: 'salmanmuneeb@gmail.com',
                 subject: "Jenkins Build Failure: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "The build failed. Please check the logs."
        }
    }
}
