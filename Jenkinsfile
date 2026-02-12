pipeline {
    agent any
    stages {
        stage('Docker Build') {
            steps {
                bat 'docker build -t framvaq/jenkins-web:latest .'
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
                    bat 'docker login -u ${env.dockerUser} -p ${env.dockerPassword}'
                    bat 'docker push framvaq/jenkins-web:latest'
                }
            }
        }
    }
}
