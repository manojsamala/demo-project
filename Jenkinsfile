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
  }
}
