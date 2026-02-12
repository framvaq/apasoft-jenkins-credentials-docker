pipeline {
    agent any
    stages {
        stage('Docker Build') {
            steps {
                pwsh 'docker build -t framirezv/jenkins-web:latest .'
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
                    pwsh "docker login -u ${env.dockerUser} -p ${env.dockerPassword}"
                    pwsh 'docker push framirezv/jenkins-web:latest'
                }
            }
        }
    }
}
