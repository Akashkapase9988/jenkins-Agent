pipeline {
    agent { label 'agent-linux' }
    options {
    timeout(time: 30, unit: 'MINUTES') 
    // some block
        }
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Akashkapase9988/java-jenkins-docker.git'

                // Run Maven on a Unix agent
                dir('Jenkins-Agent') {
                    sh "mvn clean package"
                }
            }
        }

        stage('Test') {
            steps {
                dir('Jenkins-Agent') {
                    sh "mvn test"
                }
            }
        }

        stage('Compile') {
            steps {
                dir('Jenkins-Agent') {
                    sh "mvn compile"
                }
            }
        }

        stage('Docker Build') {
            steps {
                dir('Jenkins-Agent') {
                    sh "docker build -t java-app ."
                }
            }
        }

        stage('Docker Run') {
            steps {
                dir('Jenkins-Agent') {
                    sh "docker run java-app"
                }
            }
        }
        }
    }
