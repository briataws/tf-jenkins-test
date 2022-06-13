def awesomeVersion = 'UNKNOWN'
pipeline {
  agent {
    docker {
        reuseNode true
        image 'bcarpio/terraform-kitchen'
        args '-v /etc/passwd:/etc/passwd -v /home/ec2-user/.ssh:/home/ec2-user/.ssh -v "$PWD":/usr/src/myapp -w /usr/src/myapp'
    }
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
