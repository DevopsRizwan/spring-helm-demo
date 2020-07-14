@Library('sharedlibrary@master') _
import checkout
//def checkout  = new checkout()
//pipeline([
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
    kubernetes{
          
          yaml test
    }
   }
stages{
    
    stage("Checkout"){
        steps{

            checkout.checkout([])
        }
    }
    }
}

