# jenkins-template

This is an example project to get Jenkins running in kindi/docker desktop with just about enough plugins to make it usable.

## Requirements

* helm 
* helmfile
* kind / docker desktop with kubernetes enabled

## Installation Instructions

First off, you're going to need an ingress controller - nginx will work nicely for this project and will avoid taking up too much resource.

```sh
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.46.0/deploy/static/provider/cloud/deploy.yaml
```

To install jenkins, you can run a `make diff` to see what differences are available, or

```sh
make deploy
```

To deploy changes.

## How the plugin list is defined

* Added the default min list of plugins to a plugins.txt file
* Ran `uc --jenkins-version 2.277.4 -w -d` to add transient dependencies 
* Ran `uc --jenkins-version 2.277.4 -w` to update all versions
* Add the contents of the file as the `jenkins.controller.installPlugins` block
