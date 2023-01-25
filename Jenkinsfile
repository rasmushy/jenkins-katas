pipeline {
  agent any
  stages {
    stage('clone down') {
          steps {
            stash name: 'code', excludes: '**/.git,**/.git/**'
      }
    }
    stage('Parallel execution') {
      parallel {
        stage('Say Hello') {
          steps {
            sh 'echo "hello world"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:6-jdk11'
            }

          }
          steps {
            unstash 'code'
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
          }
          options {
            skipDefaultCheckout()
          }
        }

      }
    }

  }
}