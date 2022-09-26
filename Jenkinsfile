pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/Mraim/jen', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t scver123/myweb:1.2 .
        sudo docker push scver123/myweb:1.2
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl apply -f deploy.yml
        '''
      }
    }
  }
}
