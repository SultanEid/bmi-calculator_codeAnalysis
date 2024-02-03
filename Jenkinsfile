pipeline {
  agent {
    docker {
      image 'node:18.16.0-alpine'
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
	
	stage ('Checking Snar Installation') {
	steps{
	
	
	stage('SCM') {
	    steps{
			checkout scm
		}
	  }
	  
	stage('SonarQube Analysis') {
	    steps{
			script{
				def scannerHome = tool 'SonarQube Scanner';
	    		withSonarQubeEnv() {
	    		sh "${scannerHome}/bin/sonar-scanner"
				}
			}
	    }
	  }
	
		
  }
}
