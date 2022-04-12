pipeline {
    agent all
    stages {
        stage('Deploy') {
            steps {
                docker-compose up -d
            }
        }
    }
}
pipeline {
    agent dev
    stages {
        stage('Deploy') {
            steps {
                docker-compose up -d
            }
        }
    }
}
pipeline {
    agent Prod
    stages {
        stage('Deploy') {
            steps {
                docker-compose up -d
            }
        }
    }
}
