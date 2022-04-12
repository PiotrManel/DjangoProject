node {
    stage "Create build output"
    sh "mkdir -p output"
    writeFile file: "output/usefulfile.txt", text: "This file is useful, need to archive it."
    stage "Archive build output"
    archiveArtifacts artifacts: 'output/*.txt', excludes: 'output/*.md'
}
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
