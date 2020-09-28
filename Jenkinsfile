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
                //curl -v -X GET http://localhost:8080/crumbIssuer/api/json
                 def response = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/crumbIssuer/api/json?pretty=true'
                // HttpGet httpGet = new HttpGet("http://localhost:8080/" + "crumbIssuer/api/json");
               // def host ="localhost:8080/job/FirstPipeline/job/master/buildApi"   
               // def output = JsonOutput.toJson([name: 'John', ID: 1])
              //  response = httpRequest consoleLogResponseBody: true, contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody:output, url: "http://${host}", validResponseCodes: '200'
               // println('Status: '+response.status)
                println('Response: '+response.content)
                //println(output);  
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
