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
                echo "BUILD_TIMESTAMP = $(env.BUILD_TIMESTAMP}"
            }
        }
        stage('deploy') {
            steps {
               echo 'hello Stage 3'
            }
        }
    }
}
