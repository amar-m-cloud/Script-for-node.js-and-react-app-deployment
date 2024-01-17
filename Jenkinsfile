pipeline {
    agent any

    environment {
        // Set environment variables as needed
        NODE_VERSION = 'lts'
        NPM_VERSION = '10.12.14'
        APP_NAME = 'amar-react-app'
        GIT_REPO_URL = 'https://github.com/amar-m-cloud/amar-react-app.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from Git repository
                script {
                    git branch: 'prod', url: GIT_REPO_URL
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                // Use Node.js version manager (nvm) to install specific Node.js version
                script {
                    sh "curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash"
                    sh "source ~/.nvm/nvm.sh && nvm install $NODE_VERSION && nvm use $NODE_VERSION"
                    sh "npm install -g npm@$NPM_VERSION"
                    sh "cd $APP_NAME && npm install"
                }
            }
        }

        stage('Build') {
            steps {
                // Build React app
                script {
                    sh "cd $APP_NAME && npm run build"
                }
            }
        }

        stage('Deploy') {
            steps {
                // Customize deployment steps based on your deployment environment (e.g., copy files to a server, restart services)
                // This is a basic example, adjust it according to your deployment needs
                script {
                    echo "Deploying to production server..."
                    // Add deployment steps here
                }
            }
        }
    }

    post {
        always {
            // Clean up or perform post-build actions if needed
            script {
                echo "Post-build actions..."
            }
        }
    }
}
