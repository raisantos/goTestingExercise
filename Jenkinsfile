#!/usr/bin/env groovy
pipeline{
    agent { docker { image 'golang' } }

    stages{

        stage('Dependencies'){
            steps{
                sh 'curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh'
            }
        }

        stage('Test'){
            steps{
                sh 'go test'
            }
        }

        stage('Build'){
            steps{
                sh 'go build main.go math.go -o app'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'app', onlyIfSuccessful: true
        }
    }
}