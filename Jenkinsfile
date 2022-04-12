pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'sudo docker-compose run web django-admin startproject composeexample .'
                sh 'ls -la'
                sh 'sudo docker-compose up -d'
            }
        }
    }
}
