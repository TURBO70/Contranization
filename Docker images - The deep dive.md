
![[Pasted image 20241102214925.png]]

To start a container from an image

- `docker container run`
- `docker service create


### Images are usually small

- Images have _just enought operating system_
- They normally don't include kernel
- Some images are really small:
- [Alpine image in Docker Hub](https://hub.docker.com/_/alpine)
- [Alpine Linux](https://alpinelinux.org/downloads/)


### Pulling images

- Fresh installation of Docker comes with no images
- The local repo of Docker is in `/var/lib/docker/<storage-driver>`
- Use `docker image ls` to list all of the current images in the local repo

- Use `$ docker image pull redis:latest` to pull the latest redis image
- Use `$ docker image pull alpine:latest` to pull the latest alpine linux image


### Image naming

**Image Registries**

- Images are stored in centralized places called _image registries_.
- The most common registry is [Docker Hub](https://hub.docker.com/)
- Other 3rd party registries and local registries can also be used.
- Use `$ docker info` to check the current "Registry" option.
- Image registries contain one or more _image repositories_. Each repo can have one or more versions of the image.
![[Pasted image 20241102215201.png]]
![[Pasted image 20241102215258.png]]


### Images and layers

- A Docker image is a bunch of loosely-connected read-only layers.
- Each layer is one or more files


![[Pasted image 20241102215358.png]]
![[Pasted image 20241102215427.png]]
![[Pasted image 20241102215530.png]]


### A little bit more about image hashes (digests)

- The _image_ itself is a configuration file that lists the layers and some metadata.
- The _layers_ are where the data lives (files, codes, etc.).
- Each layer is independent.
- Each image is identified by a crypto ID which is a hash of the config file.
- Each layer is identified by a crypto ID which is a has of the contents (also called _content hashes_).

- If and image or a layer is changed the hash changes.
- When pushing or pulling an image docker compresses the image to save network bandwidth - But this changes the hashes.
- That's why each layer also has a **_distribution hash_** which is the hash of the image after compression.



## Images - The commands

- `docker image pull` is the command to download images.
- `docker image ls` lists all of the images stored in your Docker host’s local image cache.
- `docker image inspect` all of the details of an image — layer data and metadata.
- `docker manifest inspect` allows you to inspect the manifest list of any image stored on Docker Hub.
- `docker buildx` is a Docker CLI plugin that extends the Docker CLI to support multi-arch builds.
- `docker image rm` is the command to delete images.