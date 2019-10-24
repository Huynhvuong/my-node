pipeline {
    environment {
    registry = "huynhvuong565/my-node"
    registryCredential = '565'
    dockerImage = ''
    }
    agent any
    triggers {
         pollSCM('* * * * *')
     }

    stages{
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
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
    }
}