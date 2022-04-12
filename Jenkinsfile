pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'sudo docker-compose run web django-admin startproject composeexample .'
                sh 'sudo chown -R $USER:$USER .'
                sh 'ls -la'
                sh 'docker-compose up -d'
            }
        }
    }
}
