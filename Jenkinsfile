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
                sh '''
                    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
                    php composer-setup.php --install-dir=/usr/local/bin --filename=composer
                    php -r "unlink('composer-setup.php');"
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies with Composer...'
                sh 'composer install --no-dev --optimize-autoloader'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'phpunit'
            }
            post {
                success {
                    junit 'application/tests/results/*.xml'
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
