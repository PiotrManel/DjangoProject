pipeline {
    agent{
        label 'dev'
    }
    stages {
        stage('Deploy') {

            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
