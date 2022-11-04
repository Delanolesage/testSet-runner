pipeline {
    agent any
    stages {
        stage("Pull latest image") {
            steps {
                sh "docker pull olatundji/testset-docker"
            }
        }
        stage("Start Grid"){
            steps {
                sh "docker-compose up -d hub chrome"
            }
        }
        stage("Run Test"){
            steps {
                sh "docker-compose up test"
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
            sh "sudo rm -rf output/"
        }
    }
}