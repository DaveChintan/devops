pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
        stage('SonarQube analysis') { 
            agent any
            steps {
                withSonarQubeEnv('Sonar') { 
                    sh '//home/chintan/Public/sonar/bin/sonar-scanner ' + 
                    '-Dsonar.projectKey=DaveChintan_devops ' +
                    '-Dsonar.organization=davechintan-github ' +
                    '-Dsonar.sources=. '+
                    '-Dsonar.host.url=https://sonarcloud.io ' +
                    '-Dsonar.login=02cce3c936c815a6ab5cf6b2f1153b68ea214a9d'
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
                   if (qg.status != 'OK') 
                   {
                     error "Pipeline aborted due to quality gate failure: ${qg.status}"
                   }
                }
            }
        }
    }
}
