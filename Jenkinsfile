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
                sh "python3 -m py_compile app.py"
            }
        }
        stage('Deploy') {
            steps {
                script {
                    input message: "Approve deployment of version ${APP_VERSION}?", 
                          ok: "Release"
                }
                echo "Deploying ${APP_NAME} version ${APP_VERSION}..."
                sh "python3 app.py"
            }
        }
    }
}
