pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
                sh 'docker-compose run web django-admin startproject composeexample .'
                sh 'ls -la'

            }
        }
    }
}
