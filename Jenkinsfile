pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Verify WAR') {
            steps {
                bat 'dir target'
            }
        }
    }
}