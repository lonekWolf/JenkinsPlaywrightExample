pipeline {
  agent { 
    docker { 
      image 'mcr.microsoft.com/playwright:v1.17.2-focal'
    } 
  }
  stages {
    stage('install playwright') {
      steps {
        sh 'npm ci'
        sh 'npx playwright test'
      }
    }
    // stage('help') {
    //   steps {
    //     sh 'npx playwright test --help'
    //   }
    // }
    // stage('test') {
    //   steps {
    //     sh '''
    //       npx playwright test --list
    //       npx playwright test
    //     '''
    //   }
    //   post {
    //     success {
    //       archiveArtifacts(artifacts: 'homepage-*.png', followSymlinks: false)
    //       sh 'rm -rf *.png'
    //     }
    //   }
    // }
  }
}
