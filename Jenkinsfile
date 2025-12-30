pipeline {
    agent any

    environment {
        // Task 5: Define where the app will be "deployed" on your machine
        DEPLOY_TARGET = "C:\\Deployments\\Flask-App"
    }

    stages {
        // Task 1: Clone the repo
        stage('Clone') {
            steps {
                checkout scm
                echo "Repository cloned successfully."
            }
        }

        // Task 2: Install dependencies
        stage('Install Dependencies') {
            steps {
                bat '''
                    python -m venv venv
                    venv\\Scripts\\python -m pip install --upgrade pip
                    venv\\Scripts\\pip install -r requirements.txt
                '''
            }
        }

        // Task 3: Run tests
        stage('Run Tests') {
            steps {
                // This assumes you have a file named test_app.py
                bat 'venv\\Scripts\\pytest'
            }
        }

        // Task 4: Build the app (Package it)
        stage('Build/Package') {
            steps {
                echo "Packaging the application..."
                // Creates a compressed archive of your code, excluding non-essential folders
                bat 'tar -czf flask_app.tar.gz --exclude=venv --exclude=.git .'
            }
        }

        // Task 5: Simulate deployment
        stage('Deploy') {
            steps {
                echo "Simulating deployment to ${env.DEPLOY_TARGET}..."
                bat """
                    if not exist "${env.DEPLOY_TARGET}" mkdir "${env.DEPLOY_TARGET}"
                    copy flask_app.tar.gz "${env.DEPLOY_TARGET}"
                    echo Deployment Complete! In a real scenario, we would unzip and restart the service here.
                """
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Check the console output for errors."
        }
    }
}
