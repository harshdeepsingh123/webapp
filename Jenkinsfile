pipeline {
  agent {
    node {
      label 'slave02'
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
    stage('Deploy'){
      steps{
          sh '/var/deployment/./deployment.sh
      }
    }
  }
}
