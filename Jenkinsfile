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
                def host ="localhost:8080/job/FirstPipeline/job/master/buildApi"   
                def output = JsonOutput.toJson([name: 'John', ID: 1])
                response = httpRequest consoleLogResponseBody: true, contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody:$output, url: "https://${host}", validResponseCodes: '200'
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
