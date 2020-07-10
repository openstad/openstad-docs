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

For instance the frontend has a .travis.yml file and de docker_publish script: https://github.com/Amsterdam/openstad-frontend/tree/development

The publish script cert environment variables are expected and can be saved in repository settings in the Travis dashboard"


## Auto deploy to cluster
It's possible, we do it for staging and release, to autodeploy to a Kubernetes cluster. See the docker_deploy file in the repository for this.

For deploy to work, the above  varaible


## Example travis file
