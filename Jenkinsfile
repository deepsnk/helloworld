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
               // curl 'http://localhost:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'  
                script {
                //curl 'http://localhost:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'  
                    
                //curl -v -X GET http://localhost:8080/crumbIssuer/api/json
                 def response = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/crumbIssuer/api/json'
                 println('Status: '+response.status)
                 println('Response: '+response.content)
                 //curl -X POST -H "Content-Type: application/json" "authentication: 'credentialsID' -d '@output' https://example/contact
                 
                //  def host ="localhost:8080/job/FirstPipeline/job/master/buildApi"   
                //  def jsonString = '{"name":"katone","age":5}'
                //  def body = 'test'
                //  def response1 = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/job/FirstPipeline/job/master/61/api/json'
                // println('Status: '+response1.status)
                // println('Response: '+response1.content)
                   
               // def slurped = new JsonSlurper().parseText(response.content)
               // print('crumbRequestField: ' +slurped.crumbRequestField)
               // print('crumb: ' +slurped.crumb)
                  cmd_exec('echo "Buils starting..."')
                  cmd_exec('curl --version')
               //  def response2 = httpRequest acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON',
              //   httpMode: 'POST', 
              //   requestBody: body, consoleLogResponseBody: true,
               //  customHeaders: [[name: 'Jenkins-Crumb', value: slurped.crumb]],
               //  url: "http://${host}",
               //  validResponseContent: 'ok'
               
              // response2 = httpRequest authentication: 'credentialsID',consoleLogResponseBody: true, contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody:jsonString, url: "http://${host}", validResponseCodes: '200'
             //  println('Status: '+response2.status)
               // println('Response: '+response1.content)
                //def slurped = new JsonSlurper().parseText(response.content)
               // print('crumbRequestField: ' +slurped.crumbRequestField)
                //print('crumb: ' +slurped.crumb)
                
                //println(output);  
                }
            }
        }
        stage('deploy') {
            steps {
               echo 'hello Stage 3'
            }
        }
        def cmd_exec(command) {
        return bat(returnStdout: true, script: "${command}").trim()
}
    }
}
