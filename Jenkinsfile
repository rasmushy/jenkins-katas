pipeline {
  agent {
    docker {
      image 'gradle:6-jdk11'
    }

  }
  stages {
    stage('Say Hello') {
      steps {
        sh 'echo "hello world"'
        sh 'ci/build-app.sh'
      }
    }

  }
}