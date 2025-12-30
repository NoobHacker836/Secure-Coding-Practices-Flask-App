pipeline {
    agent any
    stages {
        stage('Clone') {
            steps { checkout scm }
        }
        stage('Install Dependencies') {
            steps {
                // Use 'bat' for Windows or 'sh' for Linux
                bat '''
                    python -m venv venv
                    venv\\Scripts\\pip install -r requirements.txt
                '''
            }
        }
    }
}
