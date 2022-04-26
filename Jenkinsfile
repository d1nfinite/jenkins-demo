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
            agent {
                docker {
                    image 'veinmind/veinmind-runner'
                    args '--entrypoint= --mount "type=bind,source=/,target=/host,readonly,bind-propagation=rslave" -v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
            steps {
                sh '/tool/veinmind-runner scan-host jenkinsbuild'
            }
        }
    }
}