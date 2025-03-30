pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Example build step
                echo 'Building the application...'
                echo "${BRANCH_NAME}"
                // sh './gradlew build' // Replace with your build command
            }
        }

        stage('Test') {
            steps {
                // Example test step
                echo 'Running tests...'
                // sh './gradlew test' // Replace with your test command
            }
        }

        stage('Deploy') {
            steps {
                // Example deployment step
                echo 'Deploying the application...'
                // sh './deploy.sh' // Replace with your deployment script
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
