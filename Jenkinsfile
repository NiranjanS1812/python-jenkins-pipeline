pipeline {
    agent any
    environment {
        APP_NAME    = 'MyPythonApp'
        APP_VERSION = '1.2.0'
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Checking out ${APP_NAME} source code..."
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo "Running compile check on app.py..."
                // Use 'bat' for Windows instead of 'sh'
                bat "python -m py_compile app.py"
            }
        }
        stage('Deploy') {
            steps {
                script {
                    input message: "Approve deployment of version ${APP_VERSION}?", 
                          ok: "Release"
                }
                echo "Deploying ${APP_NAME} version ${APP_VERSION}..."
                // Use 'bat' for Windows instead of 'sh'
                bat "python app.py"
            }
        }
    }
}
