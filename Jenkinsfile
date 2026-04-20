pipeline {
  agent any

  environment {
    IMAGE_NAME = "my-app"
  }

  stages {

    stage('Pull Code') {
      steps {
        echo 'Code pulled from GitHub'
      }
    }

    stage('Test') {
      steps {
        echo 'Running basic tests'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -t $IMAGE_NAME:$BUILD_NUMBER .'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
        docker stop myapp || true
        docker rm myapp || true
        docker run -d -p 8085:80 --name myapp $IMAGE_NAME:$BUILD_NUMBER
        '''
      }
    }

  }
}
