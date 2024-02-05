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
	
	
	stage('SCM') {
	    steps{
			checkout scm
		}
	  }
	  

	stage('SonarQube Analysis') {
	    //tools {
        //jdk "jdk17" // the name you have given the JDK installation using the JDK manager (Global Tool Configuration)
    	//}
    	environment {
        scannerHome = tool 'SonarQube Scanner' // the name you have given the Sonar Scanner (Global Tool Configuration)
    	}

	    steps{
			script{
				def scannerHome = tool 'SonarQube Scanner';
	    		withSonarQubeEnv('SonarQube Scanner') {
	    		sh "mvn clean package sonar:sonar"
				}
			}
	    }
	  }
	
		}
  }
