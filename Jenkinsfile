pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }

        } /*
      stage('Unit tests') {
            steps {
              sh "mvn test"
               
            }
            post {
              always{
                junit 'target/surefire-reports/*.xml'
                jacoco execPattern : 'target/jacoco.exec'
              }
            }
        }       
=======
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
>>>>>>> e003f5045f91d06aa6aaa602a4da8b7d81cc3245
    }*/
  }           
    
}
