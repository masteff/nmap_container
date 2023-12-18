pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker Build') {
            steps {
                sh(script: 'docker compose build nmap')
            }
        }
        stage('Start App') {
            steps {
                sh(script: 'docker compose run --rm nmap -V')
            }
            post {
                success {
                    echo "App started"
                }
                failure {
                    eco "App could not start"
                }
            }
        }
        stage('List') {
            steps {
                sh(script: 'docker compose ps -a')
            }
        }
    }
    post {
        always {
            sh(script: 'docker compose version')
        }
    }
}