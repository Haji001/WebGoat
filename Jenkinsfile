pipeline {
    agent any
    environment {
        SONAR_HOST_URL = 'http://localhost:9000'
        SONAR_TOKEN = credentials('sqp_1d843aeb1bb902b6b99826fc3fc6e98581a83b2e')
    
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
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'
                    withSonarQubeEnv('SonarQube') {
                        sh "${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey='WebGoat' \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=${SONAR_HOST_URL} \
                            -Dsonar.login=${SONAR_TOKEN}"
                    }
                }
            }
        }
    }
}
