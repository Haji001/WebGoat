pipeline {
    agent any

    tools {
        maven 'MAVEN_3.9.6'
    }
    stages {
        stage('testing') {
            steps {
                script {
                    cleanWs()
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
