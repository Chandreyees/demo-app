pipeline {
    agent any
    tools {
        maven 'maven-3.9.9'
    }
    
    stages {
        stage ('Build Maven') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Chandreyees/demo-app']])
               bat 'mvn clean package -DskipTests'
            }
        }
        stage ('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t chandreyees20/demo-api:latest .'
                }
            }
        }
        stage('Push Image to Docker Hub') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhub-credentials', variable: 'DOCKER_HUB_PASS')]) {
                        bat 'docker login -u chandreyees20 -p %DOCKER_HUB_PASS%'
                    }
                    bat 'docker push chandreyees20/demo-api:latest'
                }
            }
        }
    }
}
