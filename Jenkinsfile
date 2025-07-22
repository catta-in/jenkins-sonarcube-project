pipeline {
    agent any

    tools {
        sonarScanner 'SonarScanner'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/catta-in/demo-playwright-workshop.git', branch: 'main'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}
