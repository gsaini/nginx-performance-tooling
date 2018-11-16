// JAVA_ARGS="-Dhudson.model.DirectoryBrowserSupport.CSP=\"sandbox allow-scripts; default-src 'unsafe-inline'; img-src * data:\""
System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "sandbox; default-src 'unsafe-inline';")


pipeline {
    agent { 
        docker { image 'node:10.13' } 
    }

    options {
        // Only keep the 5 most recent builds
        buildDiscarder(logRotator(numToKeepStr:'5'))
    }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('test') {
            steps {
                sh 'npm --version'
                sh 'printenv'
            }
        }

        stage('Performance Tests') {
            agent {
                label 'master'
            }
            when {
                branch 'master'
            }
            steps {
                deleteDir()
                checkout scm
                sh 'npm i -d'
                sh 'npm run lighthouse'
            }
            post {
                always {
                publishHTML (target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: './reports/lighthouse',
                    reportFiles: 'lighthouse-report.html',
                    reportName: "Lighthouse"
                ])
                }
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
