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
   agent any
stages{
    
    stage("Checkout"){
        steps{
         build_ci 'Rizwan'
         gitCheckout([
         git_url: "https://github.com/DevopsRizwan/Demo.git",
         git_branch: "master"
         
         ])
          
          my_function.build_ci('mavenBuild')
        }}
    }
}

