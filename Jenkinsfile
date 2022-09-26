pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }

         
          

        }   
 
    stage( 'Docker Build and Push') {
      steps {
      withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
          sh 'printenv'
         sh ' docker build -t youssef1998/madtek-app:""$GIT_COMMIT"" .'
         sh 'docker push youssef1998/madtek-app:""$GIT_COMMIT""'
      }

    }
  }           
    
}
