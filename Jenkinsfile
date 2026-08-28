pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
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
                echo "Building application..."
                bat '''
                    echo Installing dependencies / compiling...
                    echo Build step complete.
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                bat '''
                    echo Running test suite...
                    echo Test step complete.
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
    }
}
