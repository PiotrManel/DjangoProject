pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'whoami'
                sh 'ls -la'
                sh 'docker-compose up -d'
            }
        }
    }
}
