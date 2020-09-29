import groovy.json.JsonOutput
import groovy.json.JsonSlurper
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
                 def response = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/crumbIssuer/api/json'
                 //curl -X POST -H "Content-Type: application/json" "authentication: 'credentialsID' -d '@output' https://example/contact
                 def slurped = new JsonSlurper().parseText(response.content)
                  print('crumbRequestField: ' +slurped.crumbRequestField)
                  print('crumb: ' +slurped.crumb)
                  def host ="localhost:8080/job/FirstPipeline/job/master/buildApi"   
                  def jsonString = '{"name":"katone","age":5}'
                def body = 'test'
                  def response1 = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/jenkins/api/json?pretty=true'
                   def slurped1 = new JsonSlurper().parseText(response.content)
                    
               // def response1 = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',
               //  httpMode: 'POST', 
               //  requestBody: body, consoleLogResponseBody: true,
               //  url: "http://${host}",
               //  validResponseContent: 'ok'


                  //response1 = httpRequest authentication: 'credentialsID',consoleLogResponseBody: true, contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody:jsonString, url: "http://${host}", validResponseCodes: '200'
               //  println('Status: '+response1.status)
               // println('Response: '+response1.content)
               // def slurped = new JsonSlurper().parseText(response.content)
               // print('crumbRequestField: ' +slurped.crumbRequestField)
               // print('crumb: ' +slurped.crumb)
                
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
