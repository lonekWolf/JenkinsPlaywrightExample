pipeline {
  agent any
  stages {
    stage('install playwright') {
      steps {
        sh 'docker pull mcr.microsoft.com/playwright/python:v1.41.2-jammy'
        sh 'docker run mcr.microsoft.com/playwright/python:v1.41.2-jammy'
        sh '''
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }
    stage('help') {
      steps {
        sh 'npx playwright test --help'
      }
    }
    stage('test') {
      steps {
        sh '''
          npx playwright test --list
          npx playwright test
        '''
      }
      post {
        success {
          archiveArtifacts(artifacts: 'homepage-*.png', followSymlinks: false)
          sh 'rm -rf *.png'
        }
      }
    }
  }
}
