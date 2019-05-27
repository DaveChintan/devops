pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh ('printenv | sort')
            }
        }
        stage('SonarQube analysis') { 
            agent any
            steps {
                withSonarQubeEnv('Sonar') { 
                    sh '/usr/lib/sonar-scanner/bin/sonar-scanner ' + 
                    '-Dsonar.projectKey=DaveChintan_devops ' +
                    '-Dsonar.organization=davechintan-github ' +
                    '-Dsonar.sources=. '+
                    '-Dsonar.host.url=https://sonarcloud.io ' +
                    '-Dsonar.login=70cf6958a6eef1f896e59fe63679b920c64fb087'
                }
            }
        }
        stage("SonarQube Quality Gate") { 
            agent any
            steps {
               timeout(time: 1, unit: 'HOURS') 
               script
                { 
                   def qg = waitForQualityGate() 
                }
                sh {qg.status}
            }
        }
    }
}
