# How to deploy a custom image?
In case you might want to deploy your own docker image of on our more of the servers the easiest way to do this is to deploy to a custom image to a public dockerhub. Currently the Helm files assume a public dockerhub repository. If you want it be private an key for authenticating with Dockerhub, or another registry should be added.



Most likely the custom image will be a version of the Frontend. So for insance in your values yaml overwrite the name of the image:
```
frontend:
  # Deployment container is what is eventually run in the pod
  deploymentContainer:
    name: frontend
    # Docker image for this pod
    image: dockerhubname/imagename:tag
```

Run upgrade command:

```
helm upgrade  -f custom-values.yaml openstad . -n openstad
```

## Push your image automatically to dockerhub
Every repository has a travis.yml file that would work automatically if a travis account was made  dockerhub images are pushed. Both Dockerhub and Travis are free for open source project.

For instance the frontend has a .travis.yml file and de docker_publish script: https://github.com/Amsterdam/openstad-frontend/tree/development

The publish script cert environment variables, these can be saved in repository settings in the Travis dashboard:
- DOCKER_USERNAME
- DOCKER_PASSWORD


## Auto deploy to cluster
It's possible, we do it for staging and release, to autodeploy to a Kubernetes cluster. See the docker_deploy file in the repository for this.

For deploy to work, the above variables are necessary and needed to add the kubernetes config file as a variable:
- KUBE_CONFIG

This is the kubeconfig generated encoded to a base64 string. For instance can be generated like this:

`cat ${HOME}/.kube/config | base64 | pbcopy`
