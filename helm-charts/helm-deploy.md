Podtgresql-ha setup
==========

There are lots of tools that help us to achieve the postgres-ha setup like Patroni,Stolon,PostgreSQL Automatic Failover (PAF)
pgPool-II etc. 

I have tried different ha postgres charts like Patroni and repmgr+pgpool and decide to go with azure-marketplace/postgresql-ha set up because it is  making use of Pgpool-II and repmgr, which are easy to use and charts are really robust . Repmgr is used for swithover when primary node becomes unhealthy and Pgpool-II acts as a Loadbalancer and helps to reduce connection overhead.

Also incase of patroni helm chart it deloys a single db service service-ha-db with multiple satefulpods  but mono service achitecture   makes it a single point of failure where as Pgpool deploys two services as db-ha on different nodes where it creats a set of pool to overcome that issue.

How to Deploy equitativa helm chart.
----------------

```
sudo helm repo add azure-marketplace https://marketplace.azurecr.io/helm/v1/repo
sudo helm repo update
sudo helm install postgres azure-marketplace/postgresql-ha
```
By now you will be having 3 services running  primary(postgres-ha-secondary-0) and
secondary as postgres-ha-secondary-1

`alias k="sudo kubectl"` # set this alias for your ease optional


`k get svc`

```
{
NAME                                         TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)          AGE
kubernetes                                   ClusterIP      10.0.0.1       <none>          443/TCP          5d1h
myapp-equitativa                             LoadBalancer   10.0.247.207   publicIP   8080:32495/TCP   50m
postgres-postgresql-ha-pgpool                ClusterIP      10.0.185.79    <none>          5432/TCP         4h53m
postgres-postgresql-ha-postgresql            ClusterIP      10.0.68.31     <none>          5432/TCP         4h53m
postgres-postgresql-ha-postgresql-headless   ClusterIP      None           <none>          5432/TCP         4h53m

}
```




`k get pods`


```
{NAME                                           READY   STATUS    RESTARTS   AGE
myapp-equitativa-658858d954-g689f              1/1     Running   0          54m
postgres-postgresql-ha-pgpool-5d8899ff-pkqmd   1/1     Running   0          4h57m
postgres-postgresql-ha-postgresql-0            1/1     Running   0          4h57m
postgres-postgresql-ha-postgresql-1            1/1     Running   0          4h56m}

```

Login to any primary or secondary pod to grab the db crendentials

`k exec -it postgres-postgresql-ha-postgresql-1 sh`

 Execute the command `env | grep POSTGRES_PASSWORD`

Get the POSTGRES_PASSWORD
  For example you get it like POSTGRES_PASSWORD=urGJfJ5hIZ
  then Encode  "urGJfJ5hIZ" to base64

`echo -n "urGJfJ5hIZ" | base64`
 dXJHSmZKNWhJWgo==

 Yours will be different.

[^1]: Ensure you base64 is correct by using echo -n "" | base64 --decode

Replace the value at [values.yml](https://github.com/DevopsRizwan/spring-helm-demo/blame/master/helm-charts/equitativa/values.yaml#L24)


-----

Now to get the ClusterIP of DB for sql-url connection

`ClusterIP=$(k get svc postgres-postgresql-ha-postgresql -o jsonpath="{.spec.clusterIP}")`

Replace the ClusterIP at values.yml [postgresDbHost](https://github.com/DevopsRizwan/spring-helm-demo/blame/master/helm-charts/equitativa/values.yaml#L13)

Prerequisite to run equitativa 
--------

1. Get the ClusterIP
2. Get the POTGRESS_PASSWORD

I am also using init container to check if my database service is up and running;

Please refer to deployment.yml [init-container](https://github.com/DevopsRizwan/spring-helm-demo/blob/master/helm-charts/equitativa/templates/deployment.yaml#L25)


Finally; we are ready to het our deployment by 

`sudo helm install myapp ./equitativa/`

```
NAME: myapp
LAST DEPLOYED: Wed Jun 24 16:37:19 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
```

Cheers!
