pipeline {
  agent any

  tools {
    maven 'mvn-version'
  }

  stages {
    stage('Build') {
      steps {
        maven()
      }
    }
    
        stage("Build image") {
            steps {
                script {
                    build()
                    myapp = docker.build("geraldine28/ledger-service:${env.BUILD_ID}", "--build-arg VERSION=${env.BUILD_ID} .")
                }
            }
        }
    

      stage("Push image") {
        steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
                    }
               }
          }
     }
 }
  
}
