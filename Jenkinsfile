pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/SrutiGoteti/event-registration-form.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Running build steps...'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic HTML validation...'
                // Optional: you can use HTMLHint or simple checks
                script {
                    if (!fileExists('event-form.html')) {
                        error('HTML file not found!')
                    } else {
                        echo 'HTML file found. Basic test passed!'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'
                // For static demo: copy files to a simple deployment directory
                bat '''
                if not exist C:\\deploy\\event-registration mkdir C:\\deploy\\event-registration
                cp event-form.html C:\\deploy\\event-registration\\ /Y
                '''
                echo 'Deployed successfully to C:\\deploy\\event-registration'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs above.'
        }
    }
}
