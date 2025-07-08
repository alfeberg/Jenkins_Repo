pipeline {
    agent any

    parameters {
        string(name: 'USERNAME', defaultValue: 'Alcher', description: 'Your name')
        string(name: 'BRANCH', defaultValue: 'main', description: 'Git branch to build')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Deployment environment')
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
    }
}
