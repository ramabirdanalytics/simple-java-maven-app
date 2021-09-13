pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Git') {
      steps {
        sh 'git clone https://bitbucket.org/Ram75/bird/src/Bird4.0/'
        sh 'cd /var/jenkins_home/workspace/Bird4.0'
      }
    }

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Snyk') {
      steps {
        sh 'export SNYK_TOKEN=1dca7057-52a0-4712-8d4a-ea65377d7404'
        sh 'docker run --rm -it -e SNYK_TOKEN -v $(pwd):/app snyk/snyk:node snyk test --all-projects --json-file-output=/app/snyk-results.json'
      }
    }

  }
}