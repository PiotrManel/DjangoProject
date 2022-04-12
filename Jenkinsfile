pipeline {
    agent{
        label 'dev'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'whoami'
                sh 'service docker status'
                sh 'docker-compose up -d'
                sh 'docker-compose run web django-admin startproject composeexample .'
                sh 'ls -la'

            }
        }
    }
}
