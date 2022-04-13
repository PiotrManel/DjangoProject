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
                sh 'openssl req -x509 -newkey rsa:4096 -sha256 -days 3650 -nodes \
                      -keyout ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.key -out ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.crt -subj "/CN=ec2-35-159-53-144.eu-central-1.compute.amazonaws.com" \
                      -addext "subjectAltName=DNS:ec2-35-159-53-144.eu-central-1.compute.amazonaws.com,DNS:www.ec2-35-159-53-144.eu-central-1.compute.amazonaws.com,IP:35.159.53.144"'
                sh 'docker build .'
                sh 'docker-compose up -d'
                sh 'docker cp  ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.crt proxy:/etc/nginx/'
                sh 'docker cp  ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.key proxy:/etc/nginx/'
            }
        }

        stage ("Archive build output"){
            steps {
                archiveArtifacts artifacts: '*.txt'
                }
            }
        }
    }

pipeline {
    agent{
            label 'dev'
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
                    sh 'openssl req -x509 -newkey rsa:4096 -sha256 -days 3650 -nodes \
                          -keyout ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.key -out ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.crt -subj "/CN=ec2-35-159-53-144.eu-central-1.compute.amazonaws.com" \
                          -addext "subjectAltName=DNS:ec2-35-159-53-144.eu-central-1.compute.amazonaws.com,DNS:www.ec2-35-159-53-144.eu-central-1.compute.amazonaws.com,IP:35.159.53.144"'
                    sh 'docker build .'
                    sh 'docker-compose up -d'
                    sh 'docker cp  ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.crt proxy:/etc/nginx/'
                    sh 'docker cp  ec2-35-159-53-144.eu-central-1.compute.amazonaws.com.key proxy:/etc/nginx/'
                }
            }

            stage ("Archive build output"){
                steps {
                    archiveArtifacts artifacts: '*.txt'
                    }
                }
            }
        }
