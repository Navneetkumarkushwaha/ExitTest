pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Navneetkumarkushwaha/ExitTest.git'
            }
        }
        stage('Build') {
            steps {
                // Using 'sh' instead of 'bat' for cross-platform compatibility
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Using 'sh' instead of 'bat' for cross-platform compatibility
                sh 'mvn clean test'
            }
            post {
                success {
                    // Correcting 'useWrapperFileDirectly' to 'useWrapper'
                    publishHTML([
                        allowMissing: false,
                        alwaysLinkToLastBuild: false,
                        keepAll: false,
                        reportDir: 'target/surefire-reports/',
                        reportFiles: 'emailable-report.html',
                        reportName: 'HTML Report',
                        reportTitles: '',
                        useWrapper: true
                    ])
                }
            }
        }
        stage('Clean up') {
            steps {
                echo 'Clean up is done'
            }
        }
    }
}
