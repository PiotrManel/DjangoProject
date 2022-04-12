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
        stage ("Create build output") {
            steps {
                writeFile file: "buildinfo.txt", text: "test1"
                }
            }
        stage('Deploy') {
            steps {
                sh 'echo "#git repository" > buildinfo.txt'
                sh 'git branch >> buildinfo.txt'
                sh 'echo "# jenkins" >> buildinfo.txt'
                sh 'echo "buildurl = {$(pwd)}" >> buildinfo.txt'
                sh 'docker build .'
                sh 'docker-compose up -d'
            }
        }

        stage ("Archive build output"){
            steps {
                archiveArtifacts artifacts: '*.txt'
                }
            }
        }
    }
