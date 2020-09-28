import groovy.json.JsonOutput
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
                script {
                def output = JsonOutput.toJson([name: 'John', ID: 1])
                def response = httpRequest "http://httpbin.org/response-headers?param1=${output}"
                println('Status: '+response.status)
                println('Response: '+response.content)
                println(output);  
                }
            }
        }
        stage('deploy') {
            steps {
               echo 'hello Stage 3'
            }
        }
    }
}
