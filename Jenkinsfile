pipeline {
    agent any
    stages {
        stage('testing') {
            steps {
                withSonarQubeEnv(installationName: 'SonarQube Host', credentialsId: 'SONAR_TOKEN') {
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }
}
