> :warning: **This is a work in progress**: Not finished yet

Prerequisites (version matter!):
- Kubectl (1 version within digital ocean cluster version). See [Kubectl installation.](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Helm (version 3). See https://helm.sh/docs/intro/install/

Main commands are kubectl and helm.

## Installation steps

###1. Creat a Kubernetes Cluster in Digital Ocean

Select at least 3 nodes for a development cluster. Creating will take a  few minutes.

### 2. Add Config of cluster to your local machine

Once your cluster installed you can download the config file and set it to your kubectl config
If you have no cluster yet you can set the config file to the default cluster:
$HOME/.kube/config

Learn how to set up multiple config files here:
https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/#explore-the-home-kube-directory

You can also do this with digital ocean specific tool doctl:

https://github.com/digitalocean/doctl

### 3. Install Nginx-Ingress

Most cloud providers come with a load balancer for ingress. 

Easiest it to install it yourself with helm:

```
helm install nginx-ingress stable/nginx-ingress --set controller.publishService.enabled=true --set controller.scope.namespace=openstad
```



### 4. Set your DNS

Once nginx-ingress is installed DigitalOcean gives you a public IP. This is visible in your dashboard.

You can also find your IP in via your command line.

```
kubectl get svc
```

You should see something like this, look for External IP of the  ingress controller:
```
NAME                            TYPE           CLUSTER-IP       EXTERNAL-IP       PORT(S)                      AGE
kubernetes                      ClusterIP      10.999.0.1       <none>            443/TCP                      27h
nginx-ingress-controller        LoadBalancer   10.999.9.229     134.999.137.123   80:30694/TCP,443:31648/TCP   27h
nginx-ingress-default-backend   ClusterIP      10.999.223.138   <none>            80/TCP                       27h
```


Set the DNS records for following domains. 

- www.*domainname.com*
- www.api.*domainname.com*
- www.auth.*domainname.com*
- www.admin.*domainname.com*
- www.img.*domainname.com*

Advantage of first setting up domains is that Let's Encrypt configures the SSL certificates immediately.

If you have no domain, an alternative is xip.io which sends certain domain names automatically to your IP. For instance

- www.api.*178.128.136.92.xip.io*
- www.auth.*178.128.136.92.xip.io*



###5. Clone the Kubernetes Repository

Find the Kubernetes repository at https://github.com/Amsterdam/openstad-kubernetes. Clone it and go into the k8s/openstad folder. All commands and file below are present in this subdirectory.

Warning: use the **development** branch for now! (we expect to move first version to master in august 2020)



###6. Configure your custom values

Go to k8s/openstad directory.

Copy values.yaml and configure values. Create a custom-values.yaml and set the correct  values"

- Set correct base domain and set publicIp of load balancer, used for only requesting a let's encrypt certificate for hostnames if their dns is set correctly
```
## Settings for DNS
host:
  ### Base URL of the web app
  ### subdomains will be prefixed with a .
  ### to this url
  ### e.g. subdomain.example.com
  base: amsterdam.openstad.org
  publicIp: 
```

- update custom mysql password,
- Set the auth credentials, the firstLTokenLogin will allow you to login with the token into admin panel en first website. You can leave the rest empty, will be auto generated

    ### Overwrites for auth db
    auth:
      dbName: auth
      credentials:
        clientId:
        clientSecret:
        fixedUserId:
        fixedToken:
        firstLoginToken:
        adminClientId:
        adminClientSecret:

- Set basic auth user and password (used for Admin panel)

     basicAuth:
        user:
        password:


- check which containers are set, *latest one currently is development (and devel for API)*, but be aware these are auto pushed on git updates, so it might break every know and then for now. Around mid august 2020 we plan to move everything to the master branch and the latest tag and have a more stable application
- Preferrably set mail server for sending emails, but will work without on first install, so can be added later.
```
### Mail server secretes
mail:
  auth:
    host:
    port:
    user:
    secretName:
    password:

  api:
    secretName:
    host:
    port:
    user:
    emailFrom:
    adminEmailFrom:
    password:
    requireSsl:
```



### 7. Helm dependency update

Check the custom-values which dependencies you want enabled (mongodb, cert-manager and mysql).
Easiest is to leave all on. Then run the following command to install the dependencies:

```
helm dependency update
```



### 8. First installation

On first install keep certissuer to false; we are looking at a way to make this prettier in the future.

In custom-values.yml:

```
## Settings for Cert-Manager/Cluster issuer
clusterIssuer:
  enabled: false  # Whether this issuer is created
	
```

```
helm install --values custom-values.yaml --replace openstad . --namespace=openstad --create-namespace
```



Will take a few minutes to start all the pods and then run the post install database migrations

### 9. Upgrade for SSL to work

When installations is done and all pods are running you can turn on the clusterIssuer to auto generate certificates, make sure DNS works so cert-manager won't get temporarily blocked by Let's encrypt.

This way you can you check if the pods are all running
```
kubectl get pods -n openstad
```

If all are running enable clusterIssuer in custom-values. Set useProdIssuer to true to generate production SSL certificates, otherwise it will use the staging certificates of Let's encrypt.

```
## Settings for Cert-Manager/Cluster issuer
clusterIssuer:
  enabled: true  # Whether this issuer is created
  useProdIssuer: true
```
Run upgrade command:

```
helm upgrade  -f custom-values.yaml openstad . -n openstad
```



## 10. Database creation & seeds

At the moment table creation and seeding has to be done manual. There are some automatic jobs being developed to automate this proces, but for now  easiest and most stable is to run the migrations directly in the pods. (get the pod names by running kubectl get pods -n openstad)

1.1 Create the api site entries (runs both basic migrations and seeds.). This seed run will empty the tables, so don't use once running.

```
kubectl exec -n openstad -it [api-podname] node reset.js
```

2.1 Create the tables for the Auth server

```
kubectl exec -n openstad -it [auth-podname] knex migrate:latest
```

2.2 Seed the table for the Auth server. . This seed run will empty the tables, so don't use once running.

```
kubectl exec -n openstad -it [auth-podname] knex seed:run
```

3.1 Create the tables for the Image server

```
kubectl exec -n openstad -it [image-podname] knex migrate:latest
```

3.2 Seed the tables for the Image server. This seed run will empty the tables, so don't use once running.

```
kubectl exec -n openstad -it [image-podname] knex seed:run
```





## What to expect

When everything went according to plan the base domain (for example www.amsterdam.openstad.org) should show a default empty openstad site. 

If you go to /oauth/login you should should get to a login screen where you can login with the token you set in the installations process. 

The admin panel is found with admin in front of the base: www.admin.amsterdam.openstad.org. The basic auth password is set in your values file. If e-mail is working we recommend switch the auth settings for your admin panel to e-mail.



## Some other commands

For logging these commands are usefull, describe gives info like env values, logs gives the logs of the pod

```
kubectl logs [podname] -n openstad
kubectl describe [resourceType] [resourceName] -n openstad

kubectl describe pod openstad-auth-b884b985d-505ph -n openstad
kubectl logs openstad-auth-b884b985d-505ph -n openstad
```


```
helm upgrade openstad . --namespace openstad --values custom-values.yaml --kubeconfig=config.yaml
```

```
kubectl set image deployment/openstad-admin openstad-admin=openstad/admin:700636910 --record -n openstad
```

```
helm upgrade  -f custom-values.yaml openstad . -n openstad
```


```
helm get values openstad -n openstad
```

Port forwarding to access in local browser:
```
kubectl port-forward <pod_name> <local_port>:<pod_port>
kubectl port-forward openstad-admin-ccf84f977-r4b5c 9999:7777
```
This way you can access adminer in local browser

Currently fixtures are not being set properly.
Easy way to access the database to set correct config in database

```
kubectl port-forward -n openstad svc/openstad-adminer 8111:8080
```

After the command has started stating `Forwarding from 127.0.0.1:8111 -> 8080` you can open your browser to [http://localhost:8111/](http://localhost:8111/).
