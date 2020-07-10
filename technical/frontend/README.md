# Openstad Frontend
The openstad frontend is primarly built upon the ApostropheCMS, there are also a few react application that are run as modules inside ApostropheCMS. 

The main repo is found here: 



## In page editing

On of the main reasons ApostropheCMS was chosen because it easily allows for in page editing allowing for highly dynamic page.



## Multisite 

We have a custom implementation of ApostropheCMS multisite, this allows one installation to run multiple domains. As explainend in the architecture section this works together with the API and Kubernetes to make it all work. With every domain request the frontend server checks if the domain exists in cached config, if not present make a call to the Openstand API if such a domain exists, if yes it will create an express server if not/

## The Openstad version of ApostropheCMS

We have bundled. For now this is found



## ApostropheCMS documentation



The documentation of ApostropheCMS is comprehensive and good place to 