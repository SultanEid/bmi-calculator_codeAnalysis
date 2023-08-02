pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        echo 'Checkout repository '
        git(url: 'https://github.com/SultanEid/bmi-calculator_codeAnalysis.git', branch: 'master')
      }
    }

    stage('setup') {
      steps {
        echo 'Installing dependencies'
        sh 'npm install'
      }
    }

    stage('test') {
      steps {
        echo 'Running Tests'
        sh 'npm run test'
      }
    }

    stage('Build') {
      steps {
        echo 'Building'
      }
    }

  }
}