pipeline {
  agent any
  tools {
    maven 'maven' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://localhost:8081/')], contextPath: '/pipeline1', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
