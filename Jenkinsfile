pipeline {
    agent { label 'agent-linux' }

    options {
        timeout(time: 30, unit: 'MINUTES')
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    changelog: false,
                    poll: false,
                    url: 'https://github.com/Akashkapase9988/java-jenkins-docker.git'
            }
        }

        stage('Build') {
            steps {
                sh 'pwd'
                sh 'ls'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t java-app .'
            }
        }
    }
}
