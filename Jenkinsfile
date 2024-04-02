pipeline {
    agent any

    stages {
        stage('pre cleanup') {
            steps {
                sh 'docker compose down -v'
            }
        }
        stage('git scm update') {
            steps {
                git url: 'https://github.com/bamyam/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker build and push') {
            steps {
                sh'''
                docker compose up --build -d
                '''
            }
        }
    }
}
