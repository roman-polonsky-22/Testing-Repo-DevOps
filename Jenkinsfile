pipeline {
    agent any
    environment {
        // Define SonarQube scanner properties here
        SONARQUBE_SCANNER_VERSION = '4.6'
        SONAR_PROJECT_KEY = 'test'
        SONAR_HOST_URL = 'http://localhost:9000'
        SONAR_AUTH_TOKEN = 'sqp_cd7da9003f50ce7d5b08a7d50dfc591498934ac8'
        // SONAR_AUTH_TOKEN is ideally set in Jenkins credentials
    }
    stages {
        stage('Checkout') {
            steps {
                // Checking out the source code
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Your build commands go here
                echo 'Building...'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Running SonarQube scanner
                    withSonarQubeEnv('YourSonarQubeConfigurationNameInJenkins') {
                        sh "sonar-scanner \
                            -Dsonar.projectKey=${env.SONAR_PROJECT_KEY} \
                            -Dsonar.host.url=${env.SONAR_HOST_URL} \
                            -Dsonar.login=${env.SONAR_AUTH_TOKEN} \
                            -Dsonar.sourceEncoding=UTF-8 \
                            -Dsonar.sources=."
                    }
                }
            }
        }
        // Other stages like 'Test', 'Deploy', etc. can be defined here
    }
    post {
        always {
            // Post-build actions like notifications, cleanup, etc.
            echo 'The build is completed.'
        }
    }
}
