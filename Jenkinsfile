pipeline {
    agent any

    parameters {
        string(name: 'USERNAME', defaultValue: 'Alcher', description: 'Your name')
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'qa', 'prod'], description: 'Target environment')
    }

    stages {
        stage('Info') {
            steps {
                echo "Hello, ${params.USERNAME}!"
                echo "Selected Branch: ${params.BRANCH}"
                echo "Target Environment: ${params.ENVIRONMENT}"
            }
        }

        stage('Clone Repo') {
            steps {
                git branch: "${params.BRANCH}", url: 'https://github.com/alfeberg/Jenkins_Repo.git'
            }
        }

        stage('Run Script') {
            steps {
                sh 'chmod +x hello.sh'
                sh './hello.sh'
            }
        }

        // 👇 NEW STAGES
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo All tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENVIRONMENT} environment..."
                sh 'echo Deploy complete!'
            }
        }
    }
}
stage('Build Docker Image') {
    steps {
        script {
            // Build the Docker image
            sh 'docker build -t myimage:latest .'
        }
    }
}
