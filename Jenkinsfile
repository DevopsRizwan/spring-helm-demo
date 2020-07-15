#!groovy
@Library('sharedlibrary')_
//def checkout  = new checkout()
//checkout
//([
//mvnPath: "/usr/path"
//])

test = """
apiVersion: "v1"
kind: "Pod"
spec:
  containers:
  - name: node
    image: docker.io/node:latest
    imagePullPolicy: Always
    command:
    - cat
    tty: true
  

  nodeSelector:
    env: jenkins
  restartPolicy: "Never"
  securityContext: {}
  
"""
pipeline {
   agent {
    label any
   }
stages{
    
    stage("Checkout"){
        steps{
         println "echo"
        
        }}
    }
}

