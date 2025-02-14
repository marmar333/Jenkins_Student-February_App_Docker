pipeline {
    agent any

    tools {
        // Ensure that Git is installed
        git 'Default'
    }

    environment {
        // Optionally set environment variables
        // NPM_CONFIG_LOGLEVEL = 'warn'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout your Git repository
                checkout scm
            }
        }

        stage('Install NPM Dependencies') {
            steps {
                script {
                    // Install NPM dependencies
                    bat 'npm install'
                }
            }
        }

        stage('Fix NPM Vulnerabilities') {
            steps {
                script {
                    // Automatically fix vulnerabilities even if it causes breaking changes
                    bat 'npm audit fix --force'
                }
            }
        }

        stage('Run NPM Audit') {
            steps {
                script {
                    // Run npm audit to check vulnerabilities
                    bat 'npm audit'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run your tests here (you may need to adjust this step depending on your test framework)
                    bat 'npm test'
                }
            }
        }
    }

    post {
        success {
            // Any post-success actions like sending notifications
            echo 'Pipeline completed successfully.'
        }
        failure {
            // Actions to take in case of failure (e.g., sending failure notifications)
            echo 'Pipeline failed.'
        }
    }
}
