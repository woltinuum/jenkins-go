pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'golang:1.18-alpine'
                }
            }
            steps {
                script {
                    sh 'export GOCACHE=/tmp/go-cache && go build -o myapp'
                }
            }
        }
        stage('Archive') {
            agent any
            steps {
                archiveArtifacts artifacts: 'myapp', onlyIfSuccessful: true
            }
        }
    }
}
