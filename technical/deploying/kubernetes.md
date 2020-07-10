# Deploying with Kubernetes

We have developed Helm Charts for Kubernetes so it makes it easy to deploy a scalable and (relatively) vendor neutral, but standardised way of deploying. The main repository is found here: https://github.com/Amsterdam/openstad-kubernetes.

##About Kubernetes

Kubernetes is a cluster manager for docker, first developed by Google, which allows for advanced server management. For development we advice docker-compose, see getting started for that section.

We run our 5 node servers as seperate docker images, plus seperate images for mongodb, mysql and cert manager. For convenience we also package adminer to easiliy debug database