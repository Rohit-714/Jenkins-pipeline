pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Test'
          }
        }

        stage('unit testing') {
          steps {
            echo 'unit testing'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'deploy'
      }
    }

  }
}