# spring-helm-demo
This application uses spring mvc framework and postgres-ha. Deployed on AKS-
Kubernetes version- 1.15.11 using HELM

Some best practices of helm deployment has been deliberatly skipped like using 
imagePullSecrets, SecurityContext etc so that that this demo can be easily
reproducible.

How to Reproduce this on your cluster.

The project has been divided into two parts:-
<dl>
<dt>1. [Producing the docker image of spring](helm-charts/helm-deploy.md)</dt>

<dt>2. [Deploying with Helm](spring-app/image-build.md)</dt>
</dl>
Kindly follow the above two steps  to get the following

Expected output:
<img src="images/landing.png"
     alt="landing"
     style="float: left; margin-right: 10px;" />

<img src="images/db-value.png"
     alt="landing"
     style="float: left; margin-right: 10px;" />



