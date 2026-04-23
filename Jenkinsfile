pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Specifying 'main' explicitly fixes the "Couldn't find revision" error
                git branch: 'main', url: 'https://github.com/ncharshi2005-beep/lab14.git'
            }
        }

        stage('Build & Test') {
            steps {
                // 'bat' for Windows; runs clean and generates the JaCoCo reports
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            // Publishes the JUnit test results to the Jenkins UI
            junit '**/target/surefire-reports/*.xml'
            
            // Archives the JaCoCo HTML reports so you can view them in Jenkins
            archiveArtifacts artifacts: 'target/site/jacoco/**', fingerprint: true
        }
    }
}
