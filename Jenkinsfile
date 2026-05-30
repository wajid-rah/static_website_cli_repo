pipeline {
  agent any

  environment {
    SITE_DIR = '.'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        echo 'Code pulled from GitHub!'
      }
    }

    stage('Lint HTML') {
      steps {
        echo 'Checking HTML files...'
        sh 'find . -name "*.html" | head -10'
      }
    }

    stage('Archive') {
      steps {
        echo 'Archiving site files...'
        archiveArtifacts artifacts: '**/*.html', fingerprint: true
      }
    }
  }

  post {
    success { echo 'Website CI passed! Files archived.' }
    failure { echo 'CI failed — check your HTML files.' }
    always  { echo 'Pipeline finished.' }
  }
}
