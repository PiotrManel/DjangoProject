pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage ("Create build output") {
            steps {
                writeFile file: "buildinfo.txt", text: "Build info file:"
                }
            }
        stage('Deploy') {
            steps {
                sh 'echo "#git repository" >> buildinfo.txt'
                sh 'git show >> buildinfo.txt'
                sh 'echo "# jenkins" >> buildinfo.txt'
                sh 'echo "buildurl = {35.159.53.144}" >> buildinfo.txt' // XD
                sh 'echo "agentname = {${NODE_NAME}}" >> buildinfo.txt'
                sh 'echo "buildpath = {$(pwd)}" >> buildinfo.txt'
                sh 'docker build .'
                sh 'docker-compose up -d'
                sh 'docker cp buildinfo.txt Diango:/'
            }
        }

        stage ("Archive build output"){
            steps {
                archiveArtifacts artifacts: '*.txt'
                }
            }
        }
    }
