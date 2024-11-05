pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Skywalker-9/jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'gcc -o hello hello.c'
            }
        }

        stage('Test') {
            steps {
                sh './hello > output.txt'
                sh 'grep "Hello, Jenkins!" output.txt'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p /tmp/deploy'
                sh 'cp hello /tmp/deploy/'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}
