pipeline
{
    agent any

    stages
    {
        stage('Checkout')
        {
            steps
            {
                echo 'Cloning Repository from Github...'
                git branch: 'main', url: 'https://github.com/SrutiGoteti/event-registration-form.git'
            }

        }

        stage('Build')
        {
            steps
            {
                echo 'Running Build steps...'
                bat 'dir'
            }

        }

        stage('Test')
        {
            steps
            {
                echo 'Running basic HTML validation'
                script
                {
                    if(!fileExists('event-form.html'))
                    {
                        error('HTML file not found!')
                    }
                    else
                    {
                        echo 'HTML file found. Basic test passed!'
                    }
                }

            }

        }

        stage('Deploy')
        {
            steps
            {
                echo 'Deploying application'
                bat 
                '''
                if not exist C:\\deploy\\event-registration mkdir C:\\deploy\\event-registration
                copy event-form.html C:\\deploy\\event-registration\\ /Y

                '''
                echo 'Deployed application to C:\\deploy\\event-registration'
            }

        }
    }

    post
    {
        success
        {
            echo 'Pipeline Completed successfully!'
        }
        failure
        {
            echo 'Pipeline failed. Check logs above'
        }
    }
}