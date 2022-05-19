pipeline {
  agent {
    node {
      label 'window_slave_agent'
    }

  }
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
      steps {
        bat 'mvn test'
      }
    }

  }
}
