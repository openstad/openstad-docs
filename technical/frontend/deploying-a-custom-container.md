# How to deploy a custom image?
In case you might want to deploy your own docker image of on our more. Easiest way to do this is to deploy to a custom image to a public dockerhub. Currently the Helm files assume a public dockerhub repository.

In values yaml overwrite the name of the sockets:
```
deploymentContainer:
  name: api-container
  # Docker image for this pod
  image: dockerhubname/container:tag
```

Run upgrade command:

```
helm upgrade  -f custom-values.yaml openstad . -n openstad
```

## Push your image automatically to dockerhub
Every repository has a travis.yml file that would work automatically if a travis account was made  dockerhub images are pushed. Both Dockerhub and Travis are free for open source project.

For instance: https://github.com/Amsterdam/openstad-frontend


## Auto deploy to cluster
It's possible, we do it for staging and release, to autodeploy to a Kubernetes cluster.
