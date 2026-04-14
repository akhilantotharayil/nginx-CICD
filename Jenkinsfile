pipeline {
  agent any

  stages {

    stage('Build') {
      steps {
        sh 'docker build -t my-app:v1 .'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
        docker stop myapp || true
        docker rm myapp || true
        docker run -d -p 8085:80 --name myapp my-app:v1
        '''
      }
    }

  }
}
