# Deploying with Kubernetes

We deploy our servers with Kubernetes.
Kubernetes is a cluster manager for docker, first developed by Google, which allows for advanced server management.

We run our 5 node servers as separate docker images, plus separate images for mongodb, mysql and cert manager. For convenience we also package adminer to debug mysql.

We provide helm and Kubernetes config for easy deployments, they are found here: https://github.com/Amsterdam/openstad-kubernetes

See installation instructions for digitalocean to get a detailed tutorial on how to set up a Kubernetes cluster.
