
## How to build spring-helm-demo
Prerequisite to run

1. Docker installed n machine
2. Maven >3.2

Execute `./mvnw -DskipTests package`

It will create a target Jar with below output

 ```
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 8.067 s
[INFO] Finished at: 2020-06-24T17:00:32+04:00
[INFO] Final Memory: 32M/219M

 ```
---------
 Build a Docker image and push the image to Docker Hub

`docker build -t rizwanjavid/equitativa_demo_app/0.0.6`

Change the repository URL as per your credentials

`docker push <izwanjavid/equitativa_demo_app/0.0.6`

Replace the value of tag and repostory links in [Values.yaml](http://github.com/DevopsRizwan/spring-helm-demo/blame/master/helm-charts/equitativa/values.yaml#L31-L34)

That is all.