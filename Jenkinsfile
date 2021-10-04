@Library('shared-library') _
pipeline {
  agent any

  tools {
    maven 'mvn-version'
  }

  stages {
    stage('Build') {
      steps {
        mvnPackage()
      }
    }
    
        stage("Build image") {
            steps {
                script {
                    buildDocker.buildNum()
                    buildDocker.myAppDocker()
                }
            }
        }
    

      stage("Push image") {
        steps {
                script {
                    buildDocker.pushDocker()
               }
          }
     }
 }
  
}
