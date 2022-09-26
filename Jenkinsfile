pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }   
    
  stage('Unit tests') {
            steps {
              sh "mvn test"
               
           
              }
            }
    stage( 'Docker Build and Push') {
      steps {
      sh 'printenv' 
      sh 'docker build -t  youssef1998/youssefrepo' 
      sh 'docker push youssef1998/youssefrepo: madtekimage'
      }
    }
  }           
    
}
