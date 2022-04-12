node {
    stage ("Create build output") {
        sh "mkdir -p output"
        writeFile file: "output/usefulfile.txt", text: "This file is useful, need to archive it."
    }
    stage ("Archive build output"){
    archiveArtifacts artifacts: 'output/*.txt'
    }
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
                sh 'docker build .'
                sh 'docker-compose up -d'
            }
        }
            stage ("Create build output") {
                sh "mkdir -p output"
                writeFile file: "output/usefulfile.txt", text: "This file is useful, need to archive it."
            }
            stage ("Archive build output"){
            archiveArtifacts artifacts: 'output/*.txt'
            }
    }
}
