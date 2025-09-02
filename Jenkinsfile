pipeline {
    agent any
    
    tools {
        jdk 'OpenJDK8'
        maven 'Maven3'
    }
    stages {
        stage('Git Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/MangeshGot/docker-spring-boot-java-web-service-example.git']])
            }
        }
        stage('Maven Build') {
            steps {
                sh 'mvn install'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mangesh .'
            }
        }
        stage('Push onto Docker Hub with lastest tag') {
            steps {
                sh 'docker push mangeshgot/mangesh:latest'
            }
        }
        stage('Push onto Docker Hub with build number') {
            steps {
                sh 'docker push mangeshgot/mangesh:${BUILD_NUMBER}'
            }
        }
    }
}
