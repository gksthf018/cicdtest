pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/sool2/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t sool2/testweb:newnewmain .
        sudo docker push sool2/testweb:newnewmain 
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl set image deployment deploy-main ctn-main=sool2/testweb:newnewmain
        '''
      }
    }
  }
}
