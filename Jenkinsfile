pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sonar-scanner '''
                        -Dsonar.projectKey=DaveChintan_devops 
                        -Dsonar.organization=davechintan-github 
                        -Dsonar.sources=. 
                        -Dsonar.host.url=https://sonarcloud.io 
                        -Dsonar.login=02cce3c936c815a6ab5cf6b2f1153b68ea214a9d
                '''
            }
        }
    }
}
