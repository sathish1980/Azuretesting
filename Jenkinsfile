pipeline {
  agent any
  stages {
    stage("verify tooling") {
      steps {
        sh '''
          docker version
          docker info
		  docker-compose --version
          curl --version
        '''
      }
    }
    stage('Prune Docker data') {
      steps {
        sh 'docker system prune -a --volumes -f'
      }
    }
    stage('docker-compose up') {
      steps {
        sh 'docker-compose up'
      }
    }
    stage('Run tests against the container') {
      steps {
        sh 'curl http://localhost:3000'
      }
    }
  }
  
}