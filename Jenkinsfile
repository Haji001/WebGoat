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

        stage('force update') {
            steps {
                sh 'rm -rf ~/.m2/repository/*'
            }    
        }
        stage('Complete and Run SonarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    sh "sh mvn clean verify sonar:sonar -Dsonar.projectKey=WebGoat -Dsonar.projectName='WebGoat' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_62eeecfcaeab77025a8a3ed110b6f8e8d1d626b6"

                }
            }
        }
    }
}
