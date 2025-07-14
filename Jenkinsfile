pipeline {
    agent any

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Git branch to deploy')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Target environment')
    }

    environment {
        DB_HOST = 'testagfdb.cdegom4cy0q6.eu-north-1.rds.amazonaws.com'
        DB_NAME = 'agftestdb'
        DB_USER = 'postgres'
        DB_PASS = 'F3l!c!00813'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${params.BRANCH}", url: 'https://github.com/alfeberg/Jenkins_Repo.git'
            }
        }

        stage('Deploy SQL') {
            steps {
                sh '''
                export PGPASSWORD=${DB_PASS}
                psql -h ${DB_HOST} -U ${DB_USER} -d ${DB_NAME} -f db/update_script.sql
                '''
            }
        }
    }
}

