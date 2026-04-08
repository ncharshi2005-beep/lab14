pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Make sure this URL is your actual repo!
                git 'https://github.com/nharshitha728-boop/lab14'
            }
        }

        stage('Build & Test') {
            steps {
                // Use 'bat' for Windows lab PCs
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
archiveArtifacts artifacts: 'target/site/jacoco/**', fingerprint: true
        }
    }
}
