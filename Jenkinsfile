pipeline {
    agent any
environment {
    GITHUB_TOKEN = credentials('tradekish27-secret-token-text') // Use the credential ID from Jenkins
}
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
            updateGitHubStatus('success', 'Build succeeded.')
        }
        failure {
            echo 'Pipeline failed.'
            updateGitHubStatus('failure', 'Build failed.')
        }
    }
}
def updateGitHubStatus(state, description) {
    def commitSHA = env.GIT_COMMIT // Use Jenkins environment variable to fetch the current commit SHA
    def githubRepo = 'tradekish27/myBayRepo' // Replace with your GitHub repository details

    bat """
        curl -X POST -H "Authorization: token ${GITHUB_TOKEN}" -H "Content-Type: application/json" ^
        -d "{\\"state\\": \\"${state}\\",\\"description\\": \\"${description}\\",\\"context\\": \\"Jenkins Build\\",\\"target_url\\": \\"${env.BUILD_URL}\\"}" ^
        https://api.github.com/repos/${githubRepo}/statuses/${commitSHA}
    """
}

