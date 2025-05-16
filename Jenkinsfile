pipeline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/kimsihyon/source-maven-java-spring-hello-webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh '<MAVEN_BUILD_COMMAND>'
      }
    }
    stage('Test') {
      steps {
        sh '<MAVEN_TEST_COMMAND>'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', url: 'https://192.168.56.102')], contextPath: null, war: 'path/to/war'
      }
    }
  }
}
