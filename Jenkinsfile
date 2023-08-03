pipeline {
  agent {
    docker {
      image 'node:lts-bullseye-slim'
      args '-p 3000:3000'
    }

  }
  
  
  stages {
    
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/SultanEid/bmi-calculator_codeAnalysis.git', branch: 'master')
      }
    }
	
	stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'npm run test'
      }
    }
	
	stage('SCM') {
	    checkout scm
	  }
	  
	stage('SonarQube Analysis') {
	    def scannerHome = tool 'SonarScanner';
	    withSonarQubeEnv() {
	    sh "${scannerHome}/bin/sonar-scanner"
	    }
	  }
  }
}