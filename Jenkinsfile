pipeline {
    agent any

    tools {
        maven 'MAVEN_3.9.6'
    }
    stages {
        stage('clean WS') {
            steps {
                script {
                    cleanWs()
        stage('Checkout') {
            steps {
                // Checkout the source code from the GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Haji001/WebGoat.git']]])
            }
        }
        
        stage('testing') {
            steps {
                    withSonarQubeEnv(installationName: 'SonarQube Host', credentialsId: 'SONAR_TOKEN') {
                        sh 'mvn clean verify sonar:sonar \
                            -Dsonar.projectKey=WebGoat \
                            -Dsonar.projectName="WebGoat" \
                            -Dsonar.host.url=http://localhost:9000'
                    }
                }
            }
        }
    }
}
