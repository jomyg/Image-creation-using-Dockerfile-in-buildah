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
. /etc/os-release
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

> I have created a custom website with files under "/website" folder. Then i have created a "Dockerfile" file for the image creation. Please see below code for the dockerfile
```sh
FROM httpd:2.4-alpine
    
COPY ./website/ /usr/local/apache2/htdocs/

CMD ["httpd-foreground"]
```
> After creation of Dockerfile, You can build the IMAGE using below command
```sh
buildah bud -t htmlapplication
```
> Output of the build creation is:
```
STEP 1: FROM httpd:2.4-alpine
✔ docker.io/library/httpd:2.4-alpine
Trying to pull docker.io/library/httpd:2.4-alpine...
Getting image source signatures
Copying blob 242407d61b32 done
Copying blob 907dfa98a03e done
Copying blob 59bf1c3509f3 done
Copying blob 085d9bf42ab2 done
Copying blob f1ff32cc6322 done
Copying blob aa5e87b8047c done
Copying config 294cecd6c7 done
Writing manifest to image destination
Storing signatures
STEP 2: COPY ./website/ /usr/local/apache2/htdocs/
STEP 3: CMD ["httpd-foreground"]
STEP 4: COMMIT htmlapplication
Getting image source signatures
Copying blob 8d3ac3489996 skipped: already exists
Copying blob 83efd5aabbd5 skipped: already exists
Copying blob fc8c77d3c450 skipped: already exists
Copying blob 71a62b93fe7b skipped: already exists
Copying blob dede9d4fb2e9 skipped: already exists
Copying blob 5b9bda3e17e8 skipped: already exists
Copying blob 08836771dac5 done
Copying config 33c125dd42 done
Writing manifest to image destination
Storing signatures
--> 33c125dd428
Successfully tagged localhost/htmlapplication:latest
33c125dd4286095246bb5d868ebd8c6e6597654e4768d78e22c5873c436058d2
```
> Use the command "buildah images" to view the newly created IMAGE
```
REPOSITORY                TAG          IMAGE ID       CREATED          SIZE
localhost/htmlapplication latest       33c125dd4286   10 seconds ago   62.7 MB
docker.io/library/httpd   2.4-alpine   294cecd6c779   7 weeks ago      60.5 MB
```

### ⚙️ Connect with Me 

<p align="center">
<a href="mailto:jomyambattil@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/jomygeorge11"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a> 
<a href="https://www.instagram.com/therealjomy"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white"/></a><br />
