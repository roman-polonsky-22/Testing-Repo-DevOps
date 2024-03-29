node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "/Users/polonsky/Downloads/sonar-scanner-5.0.1.3006-macosx/bin/sonar-scanner"
    }
  }
}
