pipeline {
    agent any
    environment {
        DOCKER = credentials('docker')
        // DOCKER == user:pass
        // DOCKER_USR == user
        // DOCKER_PSw == pass
    }
    stages {
        stage('Docker Build') {
            steps {
                pwsh 'docker build -t framirezv/jenkins-web:latest .'
            }
        }
        stage('Docker Push') {
            steps {
                pwsh "docker login -u ${env.DOCKER_USR} -p ${env.DOCKER_PSW}"
                pwsh 'docker push framirezv/jenkins-web:latest'
            }
        }
    }
}
