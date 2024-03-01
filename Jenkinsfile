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
                    sh "mvn -Dmaven.test.failure.ignore verify sonar:sonar -Dsonar.token=$SONAR_TOKEN -Dsonar.projectKey=WebGoat -Dsonar.projectName='WebGoat' -Dsonar.host.url=http://localhost:9000"

                }
            }
        }
    }
}
