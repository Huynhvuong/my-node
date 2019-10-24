pipeline {
<<<<<<< HEAD
    environment {
    registry = "huynhvuong565/my-node"
    registryCredential = '565'
    dockerImage = ''
=======
>>>>>>> 8239ddbaf3b79c777e7c50d89d9222e5869f9347
    agent any
    tools {
        maven 'localMaven'
    }
    

    triggers {
         pollSCM('* * * * *')
     }

    stages{
<<<<<<< HEAD
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

=======
        stage('Build'){
            steps {
                sh "docker build /var/lib/jenkins/workspace/CI-with-k8s/ -t huynhvuong565/my-node:${env.BUILD_ID}"
                //sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
                sh "docker push huynhvuong565/my-node:${env.BUILD_ID}"
                sh "cd /Documents/kubernetes-course-master/ingress | kubectl create -f ."
            }
        }
>>>>>>> 8239ddbaf3b79c777e7c50d89d9222e5869f9347
    }
}
