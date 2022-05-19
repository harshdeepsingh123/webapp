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
    stage('Sonar-Report') { 
      steps {
          sh 'mvn clean install sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.analysis.mode=publish' 
       }
    }
  }
}
