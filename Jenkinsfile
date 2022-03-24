pipeline {
  agent {
    node {
      label 'windows_slave_agent'
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
     stage('Deploy') {
      steps {
        bat 'mvn clean Deploy'
      }
    }

  }
}
