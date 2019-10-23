pipeline {
    agent any
    tools {
        maven 'localMaven'
    }
    

    triggers {
         pollSCM('* * * * *')
     }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
                sh "docker build /var/lib/jenkins/workspace/Node-with-k8s/ -t huynhvuong565/my-node:${env.BUILD_ID}"
                //sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
                sh "docker push huynhvuong565/my-node:${env.BUILD_ID}"
                sh "cd /Documents/kubernetes-course-master/ingress | kubectl create -f ."
            }
        }
    }
}
