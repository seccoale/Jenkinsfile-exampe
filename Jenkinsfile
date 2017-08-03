pipeline {
  agent any
  stages {
    stage('Clean All') {
      steps {
        sh 'rm -rf .*'
        sh 'mvn clean'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn install -DskipTests'
      }
    }
    stage('Unit Test') {
      steps {
        parallel(
          "Unit Test": {
            sh 'mvn test -P unit-test'
            
          },
          "Integration": {
            sh 'mvn test -P integration-test'
            
          },
          "Feature": {
            sh 'mvn test -P feature-test'
            
          }
        )
      }
    }
    stage('TMP Stage') {
      steps {
        echo 'Fine for now'
      }
    }
  }
}