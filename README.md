# Docker tutorial

Installation will take place on a Digital Ocean droplet with Ubuntu 18.04  

## 1. Installing some tools (optional)

```bash
apt update
apt install git mc htop screen -y
```

## 2. Install docker

```bash
apt update
apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
apt update
apt-cache policy docker-ce
apt install docker-ce -y
```

To test the status of docker service:  
```
systemctl status docker
```

## 3. Run a docker image in a container

```
docker run hello-world
```

The output will be something like this

<pre>
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:41a65640635299bab090f783209c1e3a3f11934cf7756b09cb2f1e02147c6ed8
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
</pre>

Note that the container prints the message and exists immediately.

## 4. Runing a docker image with interactive shell

```
docker run -it ubuntu
```

Note that any change you make in the container is persistent between the container restarts.

## 5. List running containers

```
docker ps
```

## 6. List all containers (active and inactive)

```
docker ps -a
```

## 7. Start a stopped container

```
docker start d9b100f2f636
```

where `d9b100f2f636` is the `CONTAINER ID` that is listed in the `docker ps -a` command

## 8. Stop a running container

```
docker stop d9b100f2f636
```

where `d9b100f2f636` is the `CONTAINER ID` that is listed in the `docker ps -a` command

## 9. Remove (delete) a container

```
docker rm d9b100f2f636
```

where `d9b100f2f636` is the `CONTAINER ID` that is listed in the `docker ps -a` command

## 10. SSH into a running container

```
docker exec -it d9b100f2f636 /bin/bash
```

where `d9b100f2f636` is the `CONTAINER ID` that is listed in the `docker ps -a` command

## 11. List available images

```
docker images
```

## 12. Search for images

```
docker search ubuntu
```

Default limit is 25. To list more results use `--limit 100` option.  
The images are listed from https://hub.docker.com/  


### Useful links

- https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04
- http://phase2.github.io/devtools/common-tasks/ssh-into-a-container/
- https://www.digitalocean.com/community/tutorials/how-to-share-data-between-the-docker-container-and-the-host
- https://www.mirantis.com/blog/how-do-i-create-a-new-docker-image-for-my-application/
- https://serverfault.com/questions/924779/docker-cron-not-working
- https://github.com/francarmona/docker-ubuntu16-apache2-php7/blob/master/Dockerfile
- https://github.com/laradock/laradock
