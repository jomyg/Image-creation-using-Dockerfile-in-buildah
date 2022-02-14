# Image-creation-using-Dockerfile-in-buildah

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)]()

Buildah is a command-line tool for creating Open Container Initiatives (OCI) or traditional Docker images.You don't need Docker host or Docker-in-Docker to build container images

## Description:

Buildah is a command-line tool for building Open Container Initiative-compatible (that means Docker- and Kubernetes-compatible, too) images quickly and easily. Here an installed the buildah on Ubuntu.

## Pre-requisites:

1) You need to install and setup the Buildah.

### Installation steps I followed:

```sh
sudo apt-get -y update
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/x${ID^}_${VERSION_ID}/ /' > /etc/apt/sources.list.d/devel:kubic:libcontainers:stable.list"
wget -nv https://download.opensuse.org/repositories/devel:kubic:libcontainers:stable/x${ID^}_${VERSION_ID}/Release.key -O Release.key
sudo apt-key add - < Release.key
sudo apt-get update -qq
sudo apt-get -qq -y install buildah
```
> To check the version after buildah installation
```
buildah --version
buildah version 1.21.3 (image-spec 1.0.1-dev, runtime-spec 1.0.2-dev)
```

> You can use the command "buildah images" to view the images
```
#buildah images
REPOSITORY                TAG          IMAGE ID       CREATED         SIZE
#
```
