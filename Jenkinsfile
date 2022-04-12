pipeline {
    agent all
    stages {
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
pipeline {
    agent dev
    stages {
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
pipeline {
    agent Prod
    stages {
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
