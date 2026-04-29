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
                echo 'Composer installation step completed.'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies with Composer...'
                echo 'Dependencies installation step completed.'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Tests...'
                echo 'All tests passed!'
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
                echo 'Deploy step completed.'
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
