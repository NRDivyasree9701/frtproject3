pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the Git repository
                git branch: 'main', url: 'https://github.com/NRDivyasree9701/frtproject3.git'
            }
        }
        stage('Build') {
            steps {
                // Install dependencies and build the application
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy to a server or a deployment service
                // Example: Copy build artifacts to a server using scp
                sh 'scp -r build/ user@your_server:/path/to/deploy/'
            }
        }
        stage('Archive Artifacts') {
            steps {
                // Archive build artifacts for later use
                archiveArtifacts artifacts: '**/build/**/*', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            // Send email notification on build completion
            mail to: 'you@example.com',
                 subject: "Jenkins Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Jenkins Pipeline: ${currentBuild.fullDisplayName} (${currentBuild.result})\n\nCheck console output at ${env.BUILD_URL}"
        }
    }
}
