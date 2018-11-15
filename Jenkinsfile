pipeline {
    agent { docker { image 'node:10.13' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
    }
}
