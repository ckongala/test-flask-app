pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Set up your environment (install dependencies, etc.)
                    sh 'pip install -r requirements.txt' // Make sure to have a requirements.txt file
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run your tests here, e.g., using pytest
                    sh 'pytest' // Ensure pytest is in requirements.txt
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Add deployment logic here (e.g., copy files, restart server)
                    echo 'Deploying the application...'
                    // For example, if deploying to a server, you might use scp or ssh commands
                }
            }
        }
    }

    post {
        always {
            // Cleanup actions, if needed
            echo 'Pipeline finished.'
        }
    }
}
