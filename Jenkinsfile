pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning repository...'
            }
        }

        stage('Run Script') {
            steps {
                sh 'chmod +x hello.sh'
                sh './hello.sh'
            }
        }

        stage('Simulate Build') {
            steps {
                echo 'Simulating build...'
                sh 'sleep 2'
                echo 'Build completed successfully.'
            }
        }
    }
}
