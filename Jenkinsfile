pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/abdelkarimamghari/TP-Jenkins-Security.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install --break-system-packages -r requirements.txt || true'
            }
        }
        stage ('Run Tests') {
            steps {
                sh 'pytest'
            }
        }
        stage('SAST Scan') {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner'
                    sh "${scannerHome}/bin/sonar-scanner || true"
                }
            }
        }
        stage('SCA Scan') {
            steps {
                // Zedna --noupdate bach may-9lebch f NVD w may-blkouch
                sh 'dependency-check.sh --project "TP-Jenkins-Security" --scan . --format HTML --failOnCVSS 7 --noupdate'
            }
        }
    }
}
