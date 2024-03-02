pipeline {
    agent any

    tools {
        maven 'MAVEN_3.9.6'
    }
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
