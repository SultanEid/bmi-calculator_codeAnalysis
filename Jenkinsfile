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
	
	echo 'Installing/Updating Sonar-Scanner'
	\*sh ' set -eux SONAR_SCANNER_VERSION=4.0.0.1744'
	sh 'mkdir -p /opt '
	sh 'curl -fSL https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}.zip -o /opt/sonar-scanner.zip '
	sh 'unzip /opt/sonar-scanner.zip -d /opt'
	sh 'rm /opt/sonar-scanner.zip'
	sh' ln -s /opt/sonar-scanner-${SONAR_SCANNER_VERSION}/bin/sonar-scanner /usr/bin/sonar-scanner' 
	}
	*/
	}
	
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
