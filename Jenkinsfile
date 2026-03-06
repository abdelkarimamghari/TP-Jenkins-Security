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
        stage('SCA Scan') {
            steps {
                sh 'dependency-check.sh --project "TP-Jenkins-Security" --scan . --format HTML --failOnCVSS 7 --nvdApiKey "D205E069-7919-F111-8369-0EBF96DE670D"'
            }
        }
    }
}
