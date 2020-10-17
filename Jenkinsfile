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
                echo "BUILD_URL = ${env.BUILD_URL}"
                echo "JOB_NAME = ${env.JOB_NAME}"
              
               // curl 'http://localhost:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'  
                script {
                   pom = readMavenPom file: 'pom.xml'
                   env.POM_VERSION = pom.version

                  sh '''#!/bin/bash -xe
                      echo $POM_VERSION
                    '''.stripIndent()
                def tagName = "Backend"
                //curl 'http://localhost:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)'
                // testingStuff.print_ghibli_films()
                //curl -v -X GET http://localhost:8080/crumbIssuer/api/json
               //  def response = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/crumbIssuer/api/json'
               //  println('Status: '+response.status)
                // println('Response: '+response.content)
                 //curl -X POST -H "Content-Type: application/json" "authentication: 'credentialsID' -d '@output' https://example/contact
                 
                //  def host ="localhost:8080/job/FirstPipeline/job/master/buildApi"   
                // def jsonString = '{"name":"katone","job":"laddura}'
                    
                // def body = 'test'
                // def response1 = httpRequest authentication: 'credentialsID', url: 'http://localhost:8080/job/FirstPipeline/job/master/61/api/json'
                // println('Status: '+response1.status)
                // println('Response: '+response1.content)
                    
                 //def response2 = httpRequest authentication: 'credentialsID', url: 'http://localhost:8187/testrun?page=1&size=20'
                 //println('Status: '+response2.status)
                 //println('Response: '+response2.content)
                   
               // def slurped = new JsonSlurper().parseText(response.content)
               // print('crumbRequestField: ' +slurped.crumbRequestField)
               // print('crumb: ' +slurped.crumb)
               //   print(cmd_exec('echo "Buils starting..."'))
               //   print(cmd_exec('curl --version'))
               //   print(cmd_exec('curl -u "Testing:Testing" https://dailinkx-dev.in-technology.de/backend/dashboard/testcars'))
               //   print(cmd_exec('git rev-parse HEAD'))
                    
               //   print(cmd_exec('curl -X POST -H "Accept:application/json" https://reqres.in/api/users -d "${jsonString}"'))
              //    print(cmd_exec('curl https://reqres.in/api/users -d "name=morpheus1234&job=leader"'))
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
                 def json = "{\"buildNumber\": 151, \"tagName\": \"ASD2\"}"
                    
                    
                 def payload = JsonOutput.toJson(["buildNumber": 151, "tagName": "asasd"])
                //println(output);  
                //    "{\"rollNumber\":21 , \"firstName\":\"Saurabh\" , \"lastName\":\"Gupta\"}"
                 //print(cmd_exec('curl -k -u "Testing:Testing" -X POST https://dailinkx-dev.in-technology.de/nvhs-885/backend/testrun/buildInfo -H "Content-Type: application/json" -d "{ \\"buildNumber\\":21,\\"tagName\\":"${tagName}"}"'))
                 // print(cmd_exec('curl -u \"Testing:Testing\" -X POST \"https://dailinkx-dev.in-technology.de/nvhs-885/backend/testrun/buildInfo\" -H \"accept: application/json\" -H \"Content-Type: application/json\" -d \"{ \"buildNumber\":21, \"tagName\": \"Saurabh\"}\"'))
                }
        }
      }
        stage('deploy') {
            steps {
               echo 'hello Stage 3'
            }
        }
      }
        
        post {
         always {
            echo 'One way or another, I have finished'
            echo "BUILD_NUMBER = ${env.BUILD_NUMBER}"
            echo "BUILD_TIMESTAMP = ${env.BUILD_TIMESTAMP}"
            echo "BUILD_URL = ${env.BUILD_URL}"
            echo "JOB_NAME = ${env.JOB_NAME}"
            echo "BRANCH_NAME =${env.BRANCH_NAME}"
            echo "TAG_NAME = ${env.BRANCH_NAME}"
            print(cmd_exec('git rev-parse HEAD'))
            print(cmd_exec('grep version pom.xml'))
            script {
            def branchName = env.BRANCH_NAME
            def currentTag = 'Backend';
            def tag_name = branchName + currentTag
            echo tag_name
            pom = readMavenPom file: 'pom.xml'
            echo pom.version
            print(cmd_exec('curl -k -u "Testing:Testing" -X POST https://dailinkx-dev.in-technology.de/nvhs-885/backend/build-information/buildInfo -H "Content-Type: application/json" -d "{ \\"buildUrl\\":${BUILD_URL},\\"jobName\\":\\"$JOB_NAME\\",\\"dockerTag\\":\\"Backend\\",\\"commitId\\":\\"abc\\",\\"buildTimeStamp\\":BUILD_TIMESTAMP}"'))
            }
        }
        success {
            echo 'I succeeded!'
        }
    }
}

  def cmd_exec(command) {
              return sh(returnStdout: true, script: "${command}").trim()
   }
