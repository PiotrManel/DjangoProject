pipeline {
    agent{
        label 'Prod'
    }
    stages {
        stage ("Create build output") {
            steps {
                writeFile file: "buildinfo.txt", text: "Build info file:\n"
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
                sh 'echo "$DBPassProd"'
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
