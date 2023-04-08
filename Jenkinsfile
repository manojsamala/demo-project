pipeline{
  agent any
  stages{
    stage("Git cloning"){
      steps{
        script{
         git branch: 'main', url: 'https://github.com/manojsamala/demo-project.git'
        }
      }
    }
    stage("Unit testing"){
      steps{
        script{
          sh "mvn test"
        }
      }
    }
    stage("Integration testing"){
      steps{
        script{
          sh "mvn verify"
        } 
      }
    }
    stage("Build"){
      steps{
        script{
          sh "mvn clean install"
        }
      }
    }
    stage("Code quality test"){
      steps{
        script{
          withSonarQubeEnv(credentialsId: 'jenkins new') {
            sh "mvn clean package sonar:sonar"
          }
        }
      }
    }
    stage("upload to nexus"){
          steps{
            script{
             nexusArtifactUploader artifacts: 
               [
                 [
                   artifactId: 'springboot', 
                   classifier: '', 
                   file: 'target/Uber.jar', 
                   type: 'jar'
                 ]
               ], 
               credentialsId: 'access-token', 
               groupId: 'com.example', 
               nexusUrl: '13.235.55.44:8081', 
               nexusVersion: 'nexus3', 
               protocol: 'http', 
               repository: 'manoj_new', 
               version: '1.0.0'
               }
              }
             }
            }
          }
        
