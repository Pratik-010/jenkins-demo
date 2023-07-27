pipeline {
    agent any
    stages {
        stage ('SCM checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Pratik-010/jenkins-demo.git'
            }
        }
        stage ('docker image build') {
            steps {
                sh '/usr/bin/docker image build -t pratiek10/htmlimage .'
            }
        }
        stage ('docker auth') {
            steps {
                sh 'echo dckr_pat_zkKiPWvAKN7lgwnDLpcJZuqiDwI | docker login -u pratiek10 --password-stdin'
            }
        }
        stage ('docker push') {
            steps {
                sh 'docker image push pratiek10/htmlimage'
            }
        }
        stage ('get confirmation from user') {
            input 'Do you want to continue'
        }
        stage ('docker remove existing service') {
            steps {
                sh '/usr/bin/docker service rm service1'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name service1 -p 9090:80 --replicas 2 pratiek10/htmlimage'
            }
        }
    }
}

