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
          dir('env') {
            sh 'jx step helm build'
          }
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
          dir('env') {
            sh 'jx step helm apply'
          }
        }
      }
    }
  }
}
