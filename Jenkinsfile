pipeline {
    stages {
        stage('Deploy') {
            agent{
                label 'dev'
            }
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
