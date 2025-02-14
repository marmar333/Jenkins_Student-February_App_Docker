pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout your Git repository
                checkout scm
            }
        }

        stage('Install NPM Dependencies') {
            steps {
                // Install NPM dependencies from package.json
                bat 'npm install'
            }
        }

        stage('Fix NPM Vulnerabilities') {
            steps {
                // Fix vulnerabilities using npm audit fix with --force (may apply breaking changes)
                bat 'npm audit fix --force'
            }
        }

        stage('Run NPM Audit') {
            steps {
                // Run npm audit to check vulnerabilities
                bat 'npm audit'
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests, modify if using a different test framework
                bat 'npm test'
            }
        }
    }

    post {
        success {
            // Actions if the pipeline runs successfully
            echo 'Pipeline completed successfully.'
        }
        failure {
            // Actions if the pipeline fails
            echo 'Pipeline failed.'
        }
    }
}
