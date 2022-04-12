node {
    stage ("Create build output") {
        sh "mkdir -p output"
        writeFile file: "buildinfo.txt", text: "Build Archive"
    }
    stage ("Archive build output"){
    archiveArtifacts artifacts: '*.txt'
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
            steps {
                sh "mkdir -p output"
                writeFile file: "buildinfo.txt", text: "test1"
                writeFile file: "buildinfo.txt", text: "test2"
                }
            }
        stage ("Archive build output"){
            steps {
                archiveArtifacts artifacts: '*.txt'
                }
            }
        }
    }
