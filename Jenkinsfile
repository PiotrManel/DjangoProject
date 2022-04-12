pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'whoami'
                sh 'docker-compose run web django-admin startproject composeexample .'
                sh 'ls -la'
                sh 'docker-compose up -d'


            }
        }
    }
}
