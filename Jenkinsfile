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
         withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
        sh 'printenv'
           sh 'sudo docker build -t siddharth67/numeric-app:""$GIT_COMMIT"" .'
           sh 'docker push siddharth67/numeric-app:""$GIT_COMMIT""'
         }
       }
     }
    stage('K8S Deployment - DEV') {
       steps {
         parallel(
          "Deployment": {
           withKubeConfig([credentialsId: 'kubeconfig']) {
              sh "bash k8s-deployment.sh"
            }
           },
           "Rollout Status": {
            withKubeConfig([credentialsId: 'kubeconfig']) {
               sh "bash k8s-deployment-rollout-status.sh"
             }
          }
         )
       }
    }
  }           
    
}
