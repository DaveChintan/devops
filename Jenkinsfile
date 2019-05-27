pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
        
            steps {
                script {
                   def sonarHome = tool 'SonarQube Scanner 3'
                }
                sh (sonarHome)
            }
        }
    }
}
