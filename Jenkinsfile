pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
        
            steps {
                scripts {
                   sonarHome = tool 'SonarQube Scanner 3.3.0.1492'
                }
                sh (sonarHome)
            }
        }
    }
}
