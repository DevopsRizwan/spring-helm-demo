@Library(sharedlibrary@master) _
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
satges{
    
    stage("Checkout"){
        step{

            checkout()
        }
    }
    }
}
