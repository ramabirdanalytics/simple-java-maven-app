pipeline {
  agent any
  stages {
    stage('Git') {
      steps {
        git(url: 'https://bitbucket.org/Ram75/bird/src', branch: 'Bird4.0', credentialsId: 'ram')
      }
    }

    stage('Dependency Check') {
      steps {
        dependencyCheck(odcInstallation: 'Default', additionalArguments: '--scan "/opt/jar/" --format HTML')
        dependencyCheckPublisher()
      }
    }

  }
}