pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage('Deploy') {

            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
