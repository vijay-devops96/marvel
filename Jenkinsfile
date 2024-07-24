pipeline {
    agent { label 'agent' }

    stages {
        stage('clone') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t newimg .'
            }
        }
        stage('Delivery') {
            steps {
                sh 'aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/y7h3t1b4'
                sh 'docker tag newimg:latest public.ecr.aws/y7h3t1b4/testrepo:latest'
                sh 'docker push public.ecr.aws/y7h3t1b4/testrepo:latest'
            }
        }
    }
}
