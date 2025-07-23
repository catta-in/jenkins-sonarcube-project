pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/catta-in/demo-playwright-workshop.git', branch: 'main'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Sonar') {
                    withCredentials([string(credentialsId: 'sonar_token', variable: 'SONAR_TOKEN')]) {
                        script {
                            def scannerHome = tool 'SonarScanner'
                            sh """
                                ${scannerHome}/bin/sonar-scanner \
                                  -Dsonar.projectKey=my-jenkins-project \
                                  -Dsonar.sources=. \
                                  -Dsonar.host.url=http://sonarqube:9000 \
                                  -Dsonar.login=$SONAR_TOKEN
                            """
                        }
                    }
                }
            }
        }
    }
}
