pipeline {
  agent any

  stages {
    stage('Checkout') {
        steps {
          git branch: 'main', url: 'https://github.com/keeley-bootcamp/lbg-vat-calculator.git'
        }
    }
    stage('Install') {
        steps {
            // install react dependencies
            sh "npm install"
        }
    }
    stage('Test') {
        steps {
            // run react tests
            sh "npm test"
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
            timeout(time: 10, unit: 'MINUTES') {
                waitForQualityGate abortPipeline:true
            }   
        }
    }
  }
}