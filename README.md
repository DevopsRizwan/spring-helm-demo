# spring-helm-demo
This application uses spring mvc framework and postgres-ha. Deployed on AKS-
Kubernetes version- 1.15.11 using HELM

Some best practices of helm deployment has been deliberatly skipped like using 
imagePullSecrets, SecurityContext etc. so,  that this demo can be easily
reproducible.

How to Reproduce this on your cluster.

The project has been divided into two parts:-

1. [Producing the docker image of spring](https://github.com/DevopsRizwan/spring-helm-demo/blob/master/spring-app/README.md)

Well if you are done with image building. The main stage is deploy the app ni helm with postgresql-ha set up. Here we go 

2.  [Deploying with Helm](https://github.com/DevopsRizwan/spring-helm-demo/blob/master/helm-charts/README.md)

Kindly follow the above two steps  to get the following

Expected output:
<img src="images/landing.png"
     alt="landing"
     style="float: left; margin-right: 10px;" />

<img src="images/db-value.png"
     alt="landing"
     style="float: left; margin-right: 10px;" />



