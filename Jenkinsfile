pipeline {
    agent { label 'agent'}

    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/bamyam/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker compose build') {
            steps {
                sh 'IMAGE_NAME=bamyam/nodejsapp sudo docker compose build '
            }
        }
        stage('docker hub push') {
            steps {
                sh '''
                    sudo docker login -u bamyam -p Ba@8893389
                    sudo docker push bamyam/nodejsapp
                '''
            }
        }
        stage('microk8s run pod') {
            steps {
                sh 'microk8s kubectl run app1 --image=bamyam/nodejsapp'
            }
        }
    }
}
