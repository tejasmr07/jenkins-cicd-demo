pipeline {
    agent any

    options {
        // Keep only the last 10 builds to save disk space
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
    }

    environment {
        // Example: reference a securely stored credential without printing it
        // GITHUB_CRED = credentials('github-creds')
        APP_NAME = 'jenkins-cicd-demo'
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Checking out source code from GitHub..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}..."
                sh '''
                    echo "Installing dependencies / compiling..."
                    # Example for a Node.js app:
                    # npm install
                    # npm run build

                    # Example for a Python app:
                    # pip install -r requirements.txt

                    # Placeholder so this runs on any repo out of the box:
                    echo "Build step complete."
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh '''
                    # Example for Node.js:
                    # npm test

                    # Example for Python:
                    # pytest --junitxml=report.xml

                    echo "Test step complete."
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully."
        }
        failure {
            echo "Pipeline failed. Check the console output for the failing stage."
        }
        always {
            echo "Pipeline run finished for ${APP_NAME}."
        }
    }
}
