pipeline {
    agent any
    
    tools {
        maven 'MAVEN_3.9.6'
    }

    stages {
        stage('Test Maven') {
            steps {
                sh 'mvn --version'
            }
        }

        stage('Complete and Run SonarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=WebGoat -Dsonar.projectName='WebGoat' -Dsonar.login=$SONAR_TOKEN -Dsonar.host.url=http://localhost:9000/"
                }
            }
        }
    }
}
