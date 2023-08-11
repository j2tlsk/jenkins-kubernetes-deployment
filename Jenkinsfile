pipeline {

  environment {
    dockerimagename = "janlerski/react-app"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        github 'https://github.com/j2tlsk/jenkins-kubernetes-deployment'
      }
    }

    //stage('Build image') {
    //  steps{
    //    script {
    //      dockerImage = docker.build dockerimagename
     //   }
    //  }
   // }

    //stage('Pushing Image') {
    //  environment {
    //           registryCredential = 'dockerhub-credentials'
    //       }
     // steps{
        //script {
            //docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            //dockerImage.push("latest")
         // }
        //}
    //  }
    //}

    stage('Deploying React.js container to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", kubeconfigId: "kubernetes")
        }
      }
    }

  }

}
