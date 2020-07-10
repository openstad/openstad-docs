> :warning: **This is a work in progress**: Not finished yet

Prerequisites (version matter!):
- Kubectl (1 version within digital ocean cluster version). See [Kubectl installation.](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Helm (version 3). See https://helm.sh/docs/intro/install/

Main commands are kubectl and helm.


## 1 Create a Kubernetes Cluster in Digital Ocean
Select at least 6 nodes for a development cluster. Creating will take a  few minutes.


## 2 Add Config of cluster to your local machine
Once your cluster installed you can download the config file and set it to your kubectl config
If you have no cluster yet you can set the config file to the default cluster:
$HOME/.kube/config

Learn how to set up multiple config files here:
https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/#explore-the-home-kube-directory

## 3 Install nginx-ingress
Most cloud providers come with a load balancer for ingress. For digital ocean this needs to be installed.
Easiest way to do this is during the setup in digital ocean, it will take a few minutes to install the cluster, and then in one of the next steps.



It's also possible to install it yourself with helm:

```
helm install nginx-ingress stable/nginx-ingress --set controller.publishService.enabled=true
```

## 4 Set your DNS
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


Set the DNS records for following domains

- www.*domainname.com*
- www.api.*domainname.com*
- www.auth.*domainname.com*
- www.admin.*domainname.com*
- www.img.*domainname.com*

Advantage of first setting up domains is that Let's Encrypt configures the SSL certificates immediately.

If you have no domain, an alternative is xip.io which sends certain domain names automatically to your IP. For instance

- www.api.*178.128.136.92.xip.io*
- www.auth.*178.128.136.92.xip.io*



## Configure your custom values
Go to k8s/openstad directory.

Copy values.yaml and configure values. Create a custom-values.yaml and set the correct env values.

- Set correct base domain
```
## Settings for DNS
host:
  ### Base URL of the web app
  ### subdomains will be prefixed with a .
  ### to this url
  ### e.g. subdomain.example.com
  base: amsterdam.openstad.org
```

- update custom mysql password

- Set the auth credentials, the loginToken will allow you to login with the token into admin panel en first website.


- Set basic auth user and password (used for Admin panel)

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

- check which containers are set, *latest one currently is development (and devel for API)*, but be aware these are auto pushed on git updates, so it might break every know and then for now. Around mid august 2020 we plan to move everything to the master branch and the latest tag
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

- Set the admin login token

## Helm dependency update
Check the custom-values which dependencies you want enabled (mongodb, cert-manager and mysql).
Easiest is to leave all on. Then run the following command to install the dependencies:

```
helm dependency update
```


## First installation
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

## Upgrade for SSL to work
Wait a few minutes till all pods are running then enable certificates.

This way you can you check if the pods are all running
```
kubectl get pods -n openstad
```

If all are running enable clusterIssuer in custom-values.

```
## Settings for Cert-Manager/Cluster issuer
clusterIssuer:
  enabled: true  # Whether this issuer is created

```
Run upgrade command:

```
helm upgrade  -f custom-values.yaml openstad . -n openstad
```

## What to expect:

Domains configured should now run with standard CMS.



## What to expect

When everything went according to plan the base domain (for example www.amsterdam.openstad.org) should show a default empty openstad site. If you go to /oauth/login you should see.

## Some other commands

For logging these commands are usefull, describe gives info like env values, logs gives the logs of the pod

```
kubectl logs [podname] -n openstad
kubectl describe [resourceType] [resourceName] -n openstad

kubectl describe pod openstad-auth-b884b985d-505ph -n openstad
kubectl logs openstad-auth-b884b985d-505ph -n openstad
```


```
helm upgrade openstad . --namespace openstad --values c-values.yaml --kubeconfig=config.yaml
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
