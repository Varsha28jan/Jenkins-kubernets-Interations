

pipeline {
                          agent any
                            environment {  
                            registry = "docker.io/vmna11" 
                            registryCredential = 'dockerhub' 
                             dockerImage = ''
                                                 }
            stages {
                         stage('Hello') {
                                     steps {
                                               echo 'Hello World'
                                               }
                                               }
                         stage('git clone') {
                              steps {
                                git branch: 'main', credentialsId: 'VarshaGit', url: 'https://github.com/Varsha28jan/Jenkins-kubernets-Interations.git'
                                sh 'ls'
                                sh 'pwd'
                                                        }
                                                        }
            
        stage('Docker Build and Tag') {
                                              steps {
                                                  
                                                sh 'docker build -t mynginx .'
                                                 sh 'docker tag mynginx vmna11/mynginx1'
                                                
                                                       }
                                                       }
     /*   stage('Publish image to Docker Hub') {
                                                          steps {
                                                             withDockerRegistry([ credentialsId: "VarshaDockerId", url: "" ]) 
                                                            {
                                                             // sh 'docker push vmna11/mynginx1'
                                                              dockerImage.push()
                                                            }
                                                              }
                                                              } */
              
         stage('Deploy Image') {
           steps{
             script {
               withDockerRegistry([ credentialsId: "VarshaDockerId", url: "" ]) 
               {
               dockerImage.push()
                }
                   }
               }
           }
             
              
              
         /*     stage('Deploy to kubernetes cluster') {
                                     steps {
                                               echo 'continuous deployment'
                                       withKubeConfig([credentialsId: 'testconfig'])
       {
     
         //sh 'kubectl get pods'
         sh 'pwd'
         sh 'ls'
         sh 'cd ..'
         sh 'ls'
         sh 'kubectl apply -f newds.yaml'
         sh 'kubectl get pods'
                                       }
                                     }
              }
              
              
       //stage('deploy to rancher') {
         //echo 'deployment'
         //withKubeConfig([credentialsId: 'rancherkubeconfig', serverUrl: 'https://3.109.117.88']) {
         //sh 'kubectl apply -f /var/lib/jenkins/workspace/Final/deploymentservice.yaml'
         //sh 'kubectl get pods'
         //}
       //}
              
              
               /* stage('deploy to rancher') {
                                     steps {
                                               echo 'continuous deployment'
                                       withKubeConfig([credentialsId: 'rancher',
                    //caCertificate: '<ca-certificate>',
                    serverUrl: 'https://3.109.117.88/k8s/clusters/c-8c5n5',
                    //contextName: '<context-name>',
                    //clusterName: '<cluster-name>',
                    //namespace: '<namespace>'
                    ]) {
      sh 'kubectl apply -f /var/lib/jenkins/workspace/Final/deploymentservice.yaml'
      sh 'kubectl get pods'
    }
            }
                     }*/
              
  }
  }
