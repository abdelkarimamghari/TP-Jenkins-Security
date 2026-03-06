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
                // Hna zedna l'étape 9 dyal SonarQube
                sh 'sonar-scanner'
            }
        }
        stage('SCA Scan') {
            steps {
                // Hna 7iydna l-API key w khlina ghir l-i3dadat l-assasiya dyal l-TP
                sh 'dependency-check.sh --project "TP-Jenkins-Security" --scan . --format HTML --failOnCVSS 7'
            }
        }
    }
}
