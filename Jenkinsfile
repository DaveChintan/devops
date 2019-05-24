pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        script {
          ${node {
            stage('SCM') {
              git 'https://github.com/DaveChintan/devops.git'
            }
            stage('SonarQube analysis') {
              // requires SonarQube Scanner 2.8+
              def scannerHome = tool 'SonarQube Scanner 2.9'
              withSonarQubeEnv('My SonarQube Server') {
                sh "${scannerHome}/bin/sonar-scanner"
              }
            }
          }}
        }

      }
    }
  }
}