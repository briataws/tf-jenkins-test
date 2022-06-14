def awesomeVersion = 'UNKNOWN'
pipeline {
  agent {
    label 'ecs'
    }
  options {
    buildDiscarder(logRotator(numToKeepStr: '10'))
  }
  stages {

    stage('Test') {
      steps {
        script {
          awesomeVersion = sh(returnStdout: true, script: 'echo 0.0.1')
        }
      }
    }
  }

  post {
    failure {
      deleteDir()
      cleanWs()
    }
    success {
      deleteDir()
      cleanWs()
    }
    aborted {
      deleteDir()
      cleanWs()
    }
  }
}
