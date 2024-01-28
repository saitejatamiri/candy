pipeline {
  agent any
  tools {
    maven 'MVN_HOME' 
  }
  stages {
    stage ('Build') {
      steps {
        bat 'mvn clean install package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://localhost:8081/')], contextPath: '/pipeline2', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
