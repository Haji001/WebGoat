pipeline {
    environment {
        registry = "ant0021/testv1"
        registryCredential = 'dockerlogin'
        dockerImage = ''
    }
    agent any

    tools {
        maven 'MAVEN_3.9.6'
    }

    stages {
        stage('Clean WS') {
            steps {
                script {
                    cleanWs()
                }
            }
        }

        stage('Checkout') {
            steps {
                // Checkout the source code from the GitHub repository
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/test001']],
                    userRemoteConfigs: [[url: 'https://github.com/Haji001/WebGoat.git']]
        //         ])
        //     }
        // }

        // stage('Testing') {
        //     steps {
        //         withSonarQubeEnv(installationName: 'SonarQube Host', credentialsId: 'SONAR_TOKEN') {
        //             sh 'mvn clean verify sonar:sonar \
        //                 -Dsonar.projectKey=WebGoat \
        //                 -Dsonar.projectName="WebGoat" \
        //                 -Dsonar.login=$SONAR_TOKEN \
        //                 -Dsonar.host.url=http://localhost:9000'
                }
            }
        }
        stage('build image') {
            steps {
                script {
                  app = docker.build registry + ":$BUILD_NUMBER"
                    }
                }
            }
        }
    }
}
