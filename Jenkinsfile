pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/<your-username>/<your-repo-name>.git'
            }
        }

        stage('Build') {
            steps {
                echo '🏗️  Running build steps...'
                // Since this is a static HTML project, no compilation needed
                sh 'ls -l' // lists files so you can see event_registration_form.html in console
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running basic HTML validation...'
                // Optional: you can use HTMLHint or simple checks
                script {
                    if (!fileExists('event_registration_form.html')) {
                        error('❌ HTML file not found!')
                    } else {
                        echo '✅ HTML file found. Basic test passed!'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'
                // For static demo: copy files to a simple deployment directory
                sh '''
                mkdir -p /var/www/event-registration
                cp event_registration_form.html /var/www/event-registration/
                '''
                echo '✅ Deployed successfully to /var/www/event-registration'
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check logs above.'
        }
    }
}
