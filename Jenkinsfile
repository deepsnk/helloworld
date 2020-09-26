pipeline {
    agent any
    stages {
        stage('build') {
            steps {
               echo 'hello Stage 1'
            }
        }
        stage('test') {
            steps {
               echo 'hello Stage 2'
            }
        }
        stage('using env variables') {
            steps {
                echo "BUILD_NUMBER = ${env.BUILD_NUMBER}"
                echo "BUILD_TIMESTAMP = ${env.BUILD_TIMESTAMP}"
                def commit_id = git rev-parse HEAD
                echo "COMMIT_ID = $(commit_id)"
            }
        }
        stage('deploy') {
            steps {
               echo 'hello Stage 3'
            }
        }
    }
}
