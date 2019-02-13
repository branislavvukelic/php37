pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'We are building something now...'
                sh 'ls'
            }
        }
        stage('Test') {
            steps {
                echo 'Doing some nasty tests...'
                sh 'ls'
            }
        }
        stage('Deploy: Stage') {
            when { tag "stage-*" }
            steps {
                echo 'Deploying to stage env because this commit is tagged...'
                sh 'ls'
            }
        }
        stage('Test More') {
            when { tag "stage-*" }
            steps {
                echo 'Doing even more nasty tests...'
                sh 'ls'
            }
        }
        stage('Deploy: Prod') {
            when { tag "release-*" }
            steps {
                echo 'Deploying only because this commit is tagged...'
                sh 'rsync -avz --exclude "Jenkins*" * mrjenkins@172.16.53.203:/sites/php37.rcmteurope.com/public_html/'
            }
        }
    }
}