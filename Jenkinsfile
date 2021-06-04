pipeline {
    agent any

    stages {
        stage ('Pre-build') {
            parallel { 
                stage('Codestyle') {
                    steps {
                        sh 'make daemon-codestyle'
                        sh 'make webui-codestyle'
                    }
                }
                stage('Test') {
                    steps {
                        sh 'make daemon-unittests'
                    }
                }
            }
        }
        
        stage('Compile') {
            steps {
                sh 'make grpc daemon-compile'
            }
        }
    }
}
