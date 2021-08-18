# Installing openstad on Digital Ocean with Kubernetes

Prerequisites (version matter!):

- Kubectl (1 version within digital ocean cluster version). See [Kubectl installation.](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Helm (version 3). See https://www.digitalocean.com/community/tutorials/how-to-install-software-on-kubernetes-clusters-with-the-helm-3-package-manager

Main commands are kubectl and helm.

## Installation steps

###1. Creat a Kubernetes Cluster in Digital Ocean

Select at least 3 nodes for a development cluster. Creating will take a few minutes.

For a smaller and development installation site the default 3 nodes of $20,- per node will do. For most production environments at least 3 nodes of 40,- per months are advised, which should give 3*8GB ram and 3 * 4 CPU. Note that the default resources allocated to a pod is set low in the values.yml, so if you get a bigger machine add higher resource limits. Mainly the frontend pod could use more CPU, the image server every now and then uses a lot of memory when many images gets resized at once.

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
helm install nginx-ingress stable/nginx-ingress --set controller.publishService.enabled=true
```

Make sure you already installed the stable repository during the installation of helm:

`helm repo add stable https://kubernetes-charts.storage.googleapis.com`

It's also possible to install nginx-ingress in the wizard steps on the Digital Ocean platform.

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

- *domainname.com*
- www.*domainname.com*
- api.*domainname.com*
- auth.*domainname.com*
- admin.*domainname.com*
- img.*domainname.com*

Advantage of first setting up domains is that Let's Encrypt configures the SSL certificates immediately.

The main domain will be redirect to the non www.

For convenience sake we also advice adding a wildcard subdomain that users can use to create websites through the admin panel without having to create a DNS record every time. Cert manager will automatically generate an SSL cert. Something like this:

- \*.*openstad.denhaag.nl*

You can add this as wildcardHost, only openstad.denhaag.nl without the asterisk, below in the custom-values.yml in order for the admin panel to display this to the users.

###5. Clone the Kubernetes Repository

Find the Kubernetes repository at https://github.com/Amsterdam/openstad-kubernetes. Clone it and go into the k8s/openstad folder. All commands and file below are present in this subdirectory.



###6. Configure your custom values

Go to k8s/openstad directory.

Copy values.yaml and configure values. Create a custom-values.yaml and set the correct  values

- Set correct base domain and set publicIp of load balancer, used for only requesting a let's encrypt certificate for hostnames if their dns is set correctly, publicIp is important because the API will otherwise start to block if server makes to many requests.
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
- Set the auth credentials, the firstLoginToken will allow you to login with the token into admin panel en first website. You can leave the rest empty, will be auto generated

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


- check which containers are set, *latest one currently is v0.7.* (17-10-2020)*
- Check resources, if possible add more memory and cpu to Frontend, API and Image server.
- Set wildcard host, see previous step, for admin deployment for easy site creation: *wildcardHost*.
- Preferably set mail server for sending emails, but will work without on first install, so can be added later.
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

Will take a few minutes up till 10 minutes to start all the pods and create all the databases.

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



## 10. Mysql Table creation & seeding

At the moment table creation and seeding has to be done manual. There are some automatic jobs being developed to automate this process, but for now  easiest and most stable is to run the migrations directly in the pods.

1.1 Create the api site entries (runs both basic migrations and seeds.). This seed run will empty the tables, so don't use once running.

```
kubectl exec -n openstad -it svc/openstad-api node reset.js
```

2.1 Create the tables for the Auth server, should already be done, but no problem running it twice.

```
kubectl exec -n openstad -it svc/openstad-auth knex migrate:latest
```

2.2 Seed the table for the Auth server. This seed run will empty the tables, so don't use you have a working application

```
kubectl exec -n openstad -it svc/openstad-auth knex seed:run
```

3.1 Create the tables for the Image server.

```
kubectl exec -n openstad -it svc/openstad-image knex migrate:latest
```

3.2 Seed the tables for the Image server. This seed run will empty the tables, so don't use once running.

```
kubectl exec -n openstad -it svc/openstad-image knex seed:run
```



## What to expect

When everything went according to plan the base domain (for example www.amsterdam.openstad.org) should show a default empty openstad site.

If you go to /oauth/login you should should get to a login screen where you can login with the token you set in the installations process.

Note: this login token only works for the first site and admin panel, when creating new sites login via e-mail is necessary.

The admin panel is found with admin in front of the base: www.admin.amsterdam.openstad.org, here you can create, copy and edit sites. The basic auth password is set in your values file. If e-mail is working we recommend switch the authentication method for your admin panel to e-mail.

Every site has an /admin/login that allows for logging in with e-mail, this url also doesn't log you out. A normal login logs you out of every other site and the admin panel, if you login in as an admin you are allowed to be logged into multiple site at the same time.


## Some other commands

For logging these commands are useful, describe gives info like env values, logs gives the logs of the pod

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
kubectl port-forward -n openstad svc/openstad-api 8111:8111
```
This way you can access adminer in local browser

Easy way to access the database to set correct config in database

```
kubectl port-forward -n openstad svc/openstad-adminer 8222:8080
```

After the command has started stating `Forwarding from 127.0.0.1:8111 -> 8080` you can open your browser to [http://localhost:8111/](http://localhost:8111/).
