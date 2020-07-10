# Deploying with Kubernetes

We have chosen to move our servers to docker and deploy them with Kubernetes.
Kubernetes is a cluster manager for docker, first developed by Google, which allows for advanced server management. For development we advice docker-compose, see getting started for that section.

We run our 5 node servers as seperate docker images, plus seperate images for mongodb, mysql and cert manager. For convenience we also package adminer to easiliy debug database

> :warning: **This is a work in progress**: We are currently not yest

## Continuous Delivery

## Dockerhub
We have developed it on a kubernetes cluster for Digital Ocean, but the aim
