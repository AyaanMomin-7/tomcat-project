pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'tomcat-credentials',
                        usernameVariable: 'TOMCAT_USER',
                        passwordVariable: 'TOMCAT_PASS'
                    )
                ]) {
                    bat '''
                    curl -u %TOMCAT_USER%:%TOMCAT_PASS% ^
                    --upload-file target\\tomcat-demo-1.0.war ^
                    "http://localhost:7080/manager/text/deploy?path=/tomcat-demo&update=true"
                    '''
                }
            }
        }
    }
}