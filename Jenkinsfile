pipeline {
  agent any

  stages {
     stage('Build Artifact - Maven') {
       steps {
         sh "mvn clean package -DskipTests=true"
       archive 'target/*.jar'
     }
    }

    stage('Unit Tests - JUnit and JaCoCo') {
      steps {
        sh "mvn test"
       }
     }
    stage('Docker Build and Push') {
       steps {
         sh 'echo "hello" '
       }
     }
    stage('K8S Deployment - DEV') {
       steps {
         sh 'echo "hello" '
       }
    }
  }           
    
}
