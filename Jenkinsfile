pipeline {
    agent any

    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Building') {
            steps {
                echo 'building...'
                sleep(2)
            }
        }
        stage('Docker Build') {
            steps {
                sh(script: 'docker compose run --build nmap')
            }
        }
        stage('Finish') {
            steps {
                sleep(2)
                echo 'finished'
            }
        }
    }
}