pipeline {
  agent any
  stages {
    stage("verify tooling") {
      steps {
        sh '''
          docker version
          docker info
          curl --version
          jq --version
        '''
      }
    }
    stage('Prune Docker data') {
      steps {
        sh 'docker system prune -a --volumes -f'
      }
    }
    stage('Start container') {
      steps {
        sh 'docker-compose up -d --no-color --wait'
      }
    }
    stage('Run tests against the container') {
      steps {
        sh 'curl http://localhost:3000'
      }
    }
  }
  
}