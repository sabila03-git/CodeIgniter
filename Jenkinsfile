pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'develop', url: 'https://github.com/sabila03-git/CodeIgniter.git'
            }
        }

        stage('Install Composer') {
            steps {
                echo 'Installing Composer...'
                bat '''
                    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
                    php composer-setup.php --install-dir=C:/composer --filename=composer.phar
                    php -r "unlink('composer-setup.php');"
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies with Composer...'
                bat 'php C:/composer/composer.phar install --no-dev --optimize-autoloader'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Tests...'
                bat 'echo Tests placeholder - phpunit not required for this demo'
            }
            post {
                success {
                    echo 'Tests passed!'
                }
                failure {
                    echo 'Tests failed!'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to production environment...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
