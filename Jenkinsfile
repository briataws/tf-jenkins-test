pipeline {
  agent {
    ecs {
      inheritFrom 'ecs'
      image 'bcarpio/terraform-jnlp-slave'
    }
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '10'))
  }
  stages {

    stage('Test') {
      steps {
         sh 'terraform -v'
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
