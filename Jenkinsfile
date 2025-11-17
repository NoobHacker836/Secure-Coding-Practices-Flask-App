/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo "Building Project"
            }
        }

        stage('test') {
            steps {
                echo 'Testing Project'
            }
        }

        stage('deploy') {
            steps {
                echo 'Deploying Project'
            }
        }
    }

    post {
        // the conditions here will execute after the build is done

        always {
            //this action will happen always regardless of the result of build
            echo 'Post build condition running'
        }
        failure {
            //this action will happen only if the build has failed
            echo 'Post Action if Build failed'
        }
    }
}
