pipeline {
    agent { label 'rama' }

    stages {
        stage('clone') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t waterimg .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -itd --name spdcon -p "3030:80" waterimg'
                sh 'hostname'
            }
        }
    }
}
