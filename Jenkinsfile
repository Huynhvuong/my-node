pipeline {
  environment {
    registry = "huynhvuong565/my-node"
    registryCredential = '565'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Huynhvuong/my-node.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image && run kubectl') {
      steps{
        sh "kubectl delete -f /home/vuong/Documents/kubernetes-course-master/ingress -n default"
        sh "kubectl create -f /home/vuong/Documents/kubernetes-course-master/ingress -n default"
        //sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}