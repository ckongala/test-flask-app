pipeline {
    agent any

    environment {
        // Set environment variables if needed
        FLASK_ENV = 'development' // or 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                git url: 'https://github.com/ckongala/test-flask-app.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Install dependencies
                    sh 'pip install -r requirements.txt'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests using pytest
                    sh 'pytest test_app.py'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deployment logic here
                    echo 'Deploying the application...'
                    
                    // Example: Restarting a Flask app with Gunicorn
                    // Ensure you have Gunicorn or similar server installed
                    sh 'gunicorn -w 4 -b 0.0.0.0:5000 app:app &'
                    
                    // Add your specific deployment commands as needed
                }
            }
        }
    }

    post {
        always {
            // Actions that run after the pipeline completes
            echo 'Pipeline finished.'
        }

        success {
            echo 'The build was successful!'
        }

        failure {
            echo 'The build failed.'
        }
    }
}
