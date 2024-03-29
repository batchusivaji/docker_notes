# Docker

## Table of Contents

- [Docker](#docker)
  - [Table of Contents](#table-of-contents)
    - [Bringing up the Application to sell products online](#bringing-up-the-application-to-sell-products-online)
      - [why we are using CI/CD pipelines](#why-we-are-using-cicd-pipelines)
    - [pipeline:](#pipeline)
    - [Application Deployment – Generation Wise](#application-deployment--generation-wise)
  - [Hypervisor-based Virtualization](#hypervisor-based-virtualization)
    - [Benefits](#benefits)
    - [Limitations](#limitations)
  - [Container-based](#container-based)
    - [Runtime Isolation](#runtime-isolation)
  - [Docker Client](#docker-client)
  - [Docker Concepts](#docker-concepts)
    - [Images](#images)
    - [Containers](#containers)
    - [Registries and Repositories](#registries-and-repositories)
    - [Difference between Container and Containerization](#difference-between-container-and-containerization)
    - [Difference Conatiner and Virtual machine](#difference-conatiner-and-virtual-machine)
  - [Commands](#commands)
  - [Docker Ports \& Logging](#docker-ports--logging)
  - [Docker Images](#docker-images)
  - [Ways to Build an Image](#ways-to-build-an-image)
  - [Dockerfile](#dockerfile)
  - [Chain Run Command](#chain-run-command)
  - [Sort Multi-Lines Arguments Alphanumerically](#sort-multi-lines-arguments-alphanumerically)
  - [CMD](#cmd)
  - [Push Images to DockerHub](#push-images-to-dockerhub)
  - [Latest Tag](#latest-tag)
    - [Login](#login)
  - [Containerize An Application](#containerize-an-application)
  - [Docker Container Links](#docker-container-links)
  - [Docker Compose](#docker-compose)
  - [Docker Networking](#docker-networking)
    - [Docker Network Types](#docker-network-types)
    - [None Network](#none-network)
    - [Bridge Network Interface](#bridge-network-interface)
    - [Host Network](#host-network)
    - [Overlay Network](#overlay-network)
    - [Define Network in Compose](#define-network-in-compose)
  - [Unit Tests in Containers](#unit-tests-in-containers)
  - [Continuous Integration](#continuous-integration)
    - [Configuring Circle CI](#configuring-circle-ci)
    - [Tag the Docker Images with Two Tags](#tag-the-docker-images-with-two-tags)
  - [Running In Production](#running-in-production)
    - [Why Run It In a VM?](#why-run-it-in-a-vm)
    - [Docker Machine](#docker-machine)
    - [Creating a New VM](#creating-a-new-vm)
    - [Production deployment](#production-deployment)
    - [Extends keyword](#extends-keyword)
    - [Docker Swarm](#docker-swarm)
    - [Service Discovery](#service-discovery)
    - [Deploy Docker App In a Swarm Cluster](#deploy-docker-app-in-a-swarm-cluster)
    - [𝐇𝐞𝐫𝐞 𝐚𝐫𝐞 𝐬𝐨𝐦𝐞 𝐜𝐨𝐦𝐦𝐨𝐧 𝐞𝐫𝐫𝐨𝐫𝐬 𝐚𝐧𝐝 𝐢𝐬𝐬𝐮𝐞𝐬 𝐰𝐞 𝐨𝐟𝐭𝐞𝐧 𝐞𝐧𝐜𝐨𝐮𝐧𝐭𝐞𝐫 𝐰𝐡𝐞𝐧 𝐰𝐨𝐫𝐤𝐢𝐧𝐠 𝐰𝐢𝐭𝐡 𝐃𝐨𝐜𝐤𝐞𝐫:](#𝐇𝐞𝐫𝐞-𝐚𝐫𝐞-𝐬𝐨𝐦𝐞-𝐜𝐨𝐦𝐦𝐨𝐧-𝐞𝐫𝐫𝐨𝐫𝐬-𝐚𝐧𝐝-𝐢𝐬𝐬𝐮𝐞𝐬-𝐰𝐞-𝐨𝐟𝐭𝐞𝐧-𝐞𝐧𝐜𝐨𝐮𝐧𝐭𝐞𝐫-𝐰𝐡𝐞𝐧-𝐰𝐨𝐫𝐤𝐢𝐧𝐠-𝐰𝐢𝐭𝐡-𝐃𝐨𝐜𝐤𝐞𝐫)
    - [Docker important Commands](#docker-important-commands)


Create a nginx container with 128 MB of RAM
Create a jenkins continer with “0.5” cpu and 256 MB of RAM
docker container run  -P -d  --memory 128m nginx
docker container run --name r-memcpu-jenkins -P -d --cpus="0.5" --memory 256m jenkins/jenkins
docker stats



### Bringing up the Application to sell products online
#### why we are using CI/CD pipelines
* For example when we want to sell a product into ecommerce site there are lot of challeges will be occur
  
  ![preview](images/container1.png)
* Issues:
    1) lot of manual steps
    2) redoing the same work many times could be difficult
the above application has overcome we are using CI/CD workflow
* Continuous Deployment vs Continuous Delivery
###  pipeline:
  ![preview](images/container4.png)
### Application Deployment – Generation Wise


## Hypervisor-based Virtualization

- Physical Server
- Host OS
- Hypervisor
  - Debian
    - Libs/bins
  - Ubuntu
    - Libs/bins

### Benefits

- Cost effective
- Easy to Scale

### Limitations

- Kernel Resource Duplication
- Application Portability Issue

## Container-based

Containers share the same kernel resource.

### Runtime Isolation

- Uses only the minimal requirements
- Allows for fast deployment
- Guaranteed Portability

Example:

- Application A - Container A
  - JRE 8
  - JVM
- Application B - Container B
  - JRE 7

## Docker Client

docker build - Docker daemon
docker pull - Docker daemon
docker run - Docker daemon

Docker Daemon -> Registry (Redis) -> Redis Image
Image -> Container

Docker Daemon

Docker engine - run on remote docker daemon or local.

## Docker Concepts

### Images

- Images are read as templates used to create containers.
- Images are created with the docker build command, either by us or by other docker users.
- Images are composed of layers of other images.
- Images are stored in Docker registry.

### Containers

- If an image is a class, then a container is an instance of a class - a runtime object.
- Containers are lightweight and portable encapsulations of an environment in which to run programs.
- Containers are created from images. Inside a container, it has all the binaries and dependencies needed to run the application.

### Registries and Repositories

- A registry is where we store our images.
- You can host your own registry, or you can use Docker public registry which is called DockerHub.
- Inside a registry, images are stored repositories.
- Docker repository is a collection of different docker images with the same name, that have different tags, each tag usually means a different version of the image.
- DockerHub is a popular service for repositories.
- Official names are reviewed by DockerHub.
- If you don't specify a tag, it defaults to latest.
- Docker will use the local image first if it's available, otherwise it will download it from the network.
- 
### Difference between Container and Containerization
- Container is a Software code package containing Application's Code.it's libraries and other dependencies
-  Contanerization makes your application Portable so that the same code can run on any device 
  
### Difference Conatiner and Virtual machine


## Commands

To list available images use:

```
docker images
```

To use an image to echo "hello world":

```
docker run image echo "hello world"
```

Use -i -t for interactive.

To view currently running Docker containers use:

```
docker ps
```

To use all previous ran containers use -a.

To remove a container use:

```
docker run image --rm
```

To name a container use --name.

Use -d to run in detached mode.

To view low-level docker container information use:

```
docker inspect
```

## Docker Ports & Logging

To run docker on a specific port use:

```
docker run -it -p host_port:container_port tomcat:8.0
```

To view logs from a container use:

```
docker logs container_id
```

## Docker Images

Docker images contain a series of layers. To see the layers an image has use:

```
docker history image
```

1. All changes made to a running containers will be written to a writable layer.
2. When the container is deleted, the writable layer is also deleted, but the underlying image remains unchanged.
3. Multiple containers can share access to the same underlying image.

## Ways to Build an Image

1. Create a Dockerfile.
2. Commit changes made to a Docker container.

To commit your Docker changes use:

```
docker commit container_id repository_name:tag
```

## Dockerfile

To install an image use:

```
FROM image
```

To run a command use:

```
RUN apt-get update
```

To build a container from a Dockerfile use:

```
docker build
```



## Chain Run Command

- Each run command executes on the top writeable layer and then commits the change.
- The new image is then used for the next step in the Dockerfile.
- Each run command creates a new image layer.
- Its recommended to chain the run commands to minimize the new image layers.

## Sort Multi-Lines Arguments Alphanumerically

- This will help you avoid duplication.

## CMD

- Specifies which command to run when the container starts.
- If we don't specify the CMD command in the Dockerfile, Docker will use the default command from the image.
- The CMD instruction doesn't run when building the image.
- You can specify the command in either exec form or shell form.

## Push Images to DockerHub

- List docker images by using:

```
docker images
```

- In order to push the image you must first link the image to a Docker account.
- Name the repository something like username/repo
- To push a repo use:

```
docker tag hash_id username/repo
```

## Latest Tag

- Docker will use latest as a default tag when no tag is provided.
- A lot of repositories use it to tag the most up-to-date stable image, however,
this is still only a convention and is entirely not enforced.
- Images which are tagged latest will not be updated automatically when a newer version of the image is pushed to the repository.
- Avoid using latest tag.

### Login

To login use:

```
docker login --username=dsims
```

To push your repo use:

```
docker push username/repo
```

## Containerize An Application

To build the container use:

```
docker build -t dockerapp:v1.0 .
```

To run docker container use:

```
docker run -d -p 5000:5000 image_id
```

To find out where the docker container is running use:

```
docker-machine ls
```

To run a command inside a container use:

```
docker exec -it image_id bash
```

## Docker Container Links

Allows containers to communicate with each other. Requires a recipient container (i.e. Dockerapp) and a source container (i.e. Redis).

First run the container with:

```
docker run -d --name redis redis:3.2.0
```

Then run the Dockerapp container by using:

```
docker run -d -p 5000:5000 --link redis dockerapp:v0.3
```

Benefits of Docker Container Links:

- When you build an application with a micro-service architecture, it allows to run many
independent applications in different containers to connect with one another.
- Creates a secure tunnel between containers that doesn't need to expose any ports externally.

## Docker Compose

- Manual linking containers doesn't make sense when there's a lot of different containers (20+).
- Docker Network allows all services to connect to each other.
- Removes the burden of maintaining scripts for Docker orchestration.

To start docker services use:

```
docker-compose up
```

To view Docker compose logs use:

```
docker-compose logs
```

To stop Docker containers use:

```
docker-compose stop
```

To remove all Docker containers use:

```
docker-compose rm --all
```

To force a rebuild of an image use:

```
docker-compose build
```

## Docker Networking

Each container connects to a bridge network to connect to the host machine.

### Docker Network Types

- Closed Network / None Network
- Bridge Network
- Host Network
- Overlay Network
- under lay Network
To see Docker networks use:

```
docker network ls
```

### None Network

It's an isolated container that has no connection to the outside world.

To run a closed network use:

```
docker run -d --net none image
```

- Provides the maximum level of network protection.
- Not a good choice if network or Internet connection is required.
- Suites well when the container requires maximum level of security.

### Bridge Network Interface

To create a network use:

```
docker network create --driver bridge my_bridge_network
```

To inspect a network use:

```
docker network inspect my_bridge_network
```

To disconnect from a network use:

```
docker network disconnect bridge container_3
```

- In a bridge network containers have access to 2 network interfaces (loopback and private).
- All containers in the same network can communicate with each other.
- Containers from different bridge networks can't connect with each other by default.

### Host Network

- Least protected network model, add container to host network.
- Containers hosted on host network have full access to host's interface.
- These containers are called open containers.
- No isolation.
- Host containers have best performance.

### Overlay Network

- Supports multi-host networks out-of-the-box.
- Require some pre-existing conditions before it can be created (running in swarm mode).

### Define Network in Compose

By default it sets a single network.

## Unit Tests in Containers

- Should test some functionality in a container without any outside resources.
- Should run quickly as possible to avoid being blocked.
- Spin up quick and provide a clean and isolated environment for unit tests.

To run a service inside of a container use:

```
docker-compose run dockerapp python test.py
```

Pros:
- A single image is used throughout development and production. Increases reliability.

Cons:
- Increases size of the image.

## Continuous Integration

- Isolated changes are immediately tested and reported when they're added to a larger code base.
- Provides rapid feedback so if a bug is introduced it will be identified as soon as possible.

### Configuring Circle CI

Set DockerHub credentials in Circle CI by going to Project > Settings > Build Settings > Environmental Variables.

Then set:

```
DOCKER_HUB_EMAIL
DOCKER_HUB_PWD
DOCKER_HUB_USER_ID
```

To their respective DockerHub credentials.

### Tag the Docker Images with Two Tags

1. Git commit hash of the source code.
2. Latest

## Running In Production

Concerns:

- There are some missing pieces about Docker around data persistence, networking, security, and identity management.
- The ecosystem to support monitoring and logging are not still fully ready yet.

A lot of companies are already using Docker in production.

### Why Run It In a VM?

- To address security concerns
- Hardware level isolation

Amazon EC2 still uses VMs internally

### Docker Machine

- Can provision new VMs
- Install Docker Engine
- Configure Docker Client

### Creating a New VM

To create a new Docker VM use:

```
docker-machine create --driver digitalocean --digitalocean-access-token tag docker-app-machine
```

To setup the Docker environment use:

```
docker-machine env docker-app-machine
```

Then to see the environment variable use:

```
eval $(docker-machine env docker-app-machine)
```

### Production deployment

```
docker-compose -f prod.yml up
```

### Extends keyword

- Allows for sharing of common configurations among different files or projects.
- Can be useful if you have several different environments that re-use most configuration options.

Use:

```
extends:
  file: common.yml
  service: redis
```

### Docker Swarm

- A tool that clusters many Docker Engines and scheduled containers.
- Decides which host to run the container based on scheduling methods.

Set Digital Ocean configuration information by using:

```
export DIGITALOCEAN_ACCESS_TOKEN=
export DIGITALOCEAN_PRIVATE_NETWORKING=true
export DIGITALOCEAN_IMAGE=
```

### Service Discovery

- Key component of most distributed systems and service oriented architectures.
- In the context of Docker Swarm, service discovery is about how the Swarm Manager keeps track of the state of all the nodes in a cluster.

### Deploy Docker App In a Swarm Cluster

1. Provision a consul machine and run machine as a key-value store for service discovery.
2. Provision a Docker swarm master node.
3. Provision a Docker swarm slave node.
4. Define the overlay network to support multi-host networking.
5. Deploy out Docker app services on the Swarm cluster via Docker compose.

To display the network configuration use:

```
docker-machine ssh consul ifconfig
```

To ping the private and public IPs use:

```
ping -c 1 $(docker-machine ssh consul 'ifconfig eth0 | grep "inet addr:" | cut -d: -f2 | cut -d" " -f1')
ping -c 1 $(docker-machine ssh consul 'ifconfig eth1 | grep "inet addr:" | cut -
```

To configure Docker client to connect to consul use:

```
eval $(docker-machine env consul)
```

To create a Swarm master node use:

```
docker-machine create -d digitalocean --swarm --swarm-master --swarm-discovery="consul://${KP_IP}:8500" --engine-opt="cluster-store=consul://${KP_IP}:8500" --engine-opt="cluster-advertise=eth1:2376" master
```

To create slave nodes use:

```
docker-machine create -d digitalocean --swarm --swarm-discovery="consul://${KP_IP}:8500" --engine-opt="cluster-store=consul://${KP_IP}:8500" --engine-opt="cluster-advertise=eth1:2376" slave
```

### 𝐇𝐞𝐫𝐞 𝐚𝐫𝐞 𝐬𝐨𝐦𝐞 𝐜𝐨𝐦𝐦𝐨𝐧 𝐞𝐫𝐫𝐨𝐫𝐬 𝐚𝐧𝐝 𝐢𝐬𝐬𝐮𝐞𝐬 𝐰𝐞 𝐨𝐟𝐭𝐞𝐧 𝐞𝐧𝐜𝐨𝐮𝐧𝐭𝐞𝐫 𝐰𝐡𝐞𝐧 𝐰𝐨𝐫𝐤𝐢𝐧𝐠 𝐰𝐢𝐭𝐡 𝐃𝐨𝐜𝐤𝐞𝐫:

1.𝐈𝐦𝐚𝐠𝐞 𝐍𝐨𝐭 𝐅𝐨𝐮𝐧𝐝: You might encounter this error when trying to run a container with an image that doesn't exist locally or on the specified Docker registry. Ensure that you've pulled the image or that the image name and tag are correct.

2.𝐏𝐞𝐫𝐦𝐢𝐬𝐬𝐢𝐨𝐧 𝐃𝐞𝐧𝐢𝐞𝐝: Docker containers often run as non-root users for security reasons. If your application requires access to certain resources or directories, make sure you've set the appropriate file permissions and user/group settings within the container.

3.𝐏𝐨𝐫𝐭 𝐂𝐨𝐧𝐟𝐥𝐢𝐜𝐭𝐬: Trying to run multiple containers that use the same host port can lead to port conflicts. Ensure that the ports you specify in the docker run command do not conflict with existing ports in use on your host system.

4.𝐎𝐮𝐭 𝐨𝐟 𝐃𝐢𝐬𝐤 𝐒𝐩𝐚𝐜𝐞: Docker uses disk space for images, containers, and logs. Over time, this can consume a significant amount of disk space. Periodically clean up unused images and containers using the docker system prune command.

5.𝐂𝐨𝐧𝐭𝐚𝐢𝐧𝐞𝐫 𝐂𝐫𝐚𝐬𝐡: Containers may crash for various reasons, such as misconfiguration or application issues. Use docker logs <container_name> to check the container logs for error messages that can help diagnose the problem.

6.𝐃𝐨𝐜𝐤𝐞𝐫 𝐁𝐮𝐢𝐥𝐝 𝐅𝐚𝐢𝐥𝐮𝐫𝐞𝐬: Issues may arise during the build process of a Docker image. Common problems include incorrect Dockerfile syntax, missing files or dependencies, and network problems while downloading packages during the build.

7.𝐍𝐞𝐭𝐰𝐨𝐫𝐤𝐢𝐧𝐠 𝐏𝐫𝐨𝐛𝐥𝐞𝐦𝐬: Docker containers can have connectivity problems if not properly configured. Ensure that the container is attached to the correct network, that firewalls are not blocking required ports, and that DNS settings are correct.

8.𝐕𝐨𝐥𝐮𝐦𝐞 𝐌𝐨𝐮𝐧𝐭 𝐄𝐫𝐫𝐨𝐫𝐬: Failing to properly mount volumes can result in data loss or incorrect behavior. Double-check the paths and permissions when using the -v flag in docker run or docker-compose.

9.𝐑𝐞𝐬𝐨𝐮𝐫𝐜𝐞 𝐂𝐨𝐧𝐬𝐭𝐫𝐚𝐢𝐧𝐭𝐬: Docker containers can consume significant CPU and memory resources. Make sure you allocate appropriate resources using the --cpu and --memory flags when running containers.

10.𝐈𝐦𝐚𝐠𝐞 𝐕𝐮𝐥𝐧𝐞𝐫𝐚𝐛𝐢𝐥𝐢𝐭𝐢𝐞𝐬: Using outdated or insecure base images can introduce security vulnerabilities. Regularly update your Docker images and use tools like Clair or Trivy to scan for vulnerabilities.

11.𝐑𝐞𝐬𝐨𝐮𝐫𝐜𝐞 𝐋𝐞𝐚𝐤𝐬: Containers should clean up after themselves when they exit. Be cautious about resource leaks, such as leaving behind orphaned processes or unreleased file handles.


### Docker important Commands

 Docker 50 commands
 _________________
- docker run - run a container from an image
- docker pull - pull an image from a registry
- docker push - push an image to a registry
- docker build - build an image from a Dockerfile
- docker ps - list running containers
- docker stop - stop a running container
- docker start - start a stopped container
- docker restart - restart a container
- docker logs - show the logs of a container
- docker exec - execute a command inside a running container
- docker images - list available images
- docker rm - remove a container
- docker rmi - remove an image
- docker inspect - show information about a container
- docker network create - create a network for containers to communicate
- docker network connect - connect a container to a network
- docker network disconnect - disconnect a container from a network
- docker port - show the mapped ports of a container
- docker cp - copy files between a container and the host
- docker commit - create a new image from a container's changes
- docker login - log in to a registry
- docker logout - log out of a registry
- docker tag - tag an image with a new name
- docker export - export the contents of a container as a tar archive
- docker import - create a new image from a tar archive
- docker save - save an image as a tar archive
- docker load - load an image from a tar archive
- docker top - show the processes running inside a container
- docker stats - show resource usage statistics of containers
- docker diff - show the changes made to a container's filesystem
- docker events - show the events generated by Docker
- docker history - show the history of an image
- docker pause - pause a running container
- docker unpause - unpause a paused container
- docker kill - send a signal to a container to stop it abruptly
- docker wait - wait for a container to exit and return its exit code
- docker attach - attach to a running container's console
- docker buildx - build and push multi-platform images
- docker compose - manage multi-container applications with Docker Compose
- docker swarm - create and manage a cluster of Docker nodes
- docker volume create - create a named volume for persistent data storage
- docker volume ls - list available volumes
- docker volume rm - remove a named volume
- docker system prune - remove all unused objects from Docker
- docker system df - show the usage of Docker objects
- docker system events - show the events generated by Docker on the system
- docker system info - show the system-wide information about Docker
- docker system inspect - show detailed information about Docker objects
- docker system logs - show the system logs of Docker
- docker system version - show the version of Docker installed on the system

