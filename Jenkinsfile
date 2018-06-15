pipeline {
  agent {
    label "jenkins-maven"
  }
  environment {
      DEPLOY_NAMESPACE = 'jx-staging'
  }
  stages {
    stage('Validate Environment') {
      steps {
        container('maven') {
          //sh 'make build'
          sh 'jx step helm build --dir env"
        }
      }
    }
    stage('Update Environment') {
      when {
        branch 'master'
      }
      steps {
        container('maven') {
          //sh 'make install'
          sh 'jx step helm apply --dir env"
        }
      }
    }
  }
}
