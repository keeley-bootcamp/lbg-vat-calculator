pipeline {
  agent any

  stages {
    stage('Checkout') {
        steps {
            // github repo
          git branch: 'main', url: 'https://github.com/keeley-bootcamp/lbg-vat-calculator.git'
        }
    }
    stage('SonarQube Analysis') {
      environment {
        scannerHome = tool 'sonarqube'
      }
        steps {
            withSonarQubeEnv('sonar-qube-1') {        
              sh "${scannerHome}/bin/sonar-scanner"
            }   
        }
    }
  }
}