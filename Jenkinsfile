pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                script {
                    docker.build("jenkinsbuild")
                }
            }
        }

        stage('scan') {
            steps {
                script {
                    sh 'docker run -v /:/host -v /var/run/docker.sock:/var/run/docker.sock veinmind/veinmind-runner scan-host jenkinsbuild'
                }
            }
        }
    }
}