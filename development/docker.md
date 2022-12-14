# Docker

## Introduction

- [Docker website](https://www.docker.com/)
- [Docker Documentation](https://docs.docker.com/)

### What is Docker?

Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

This means the application will run on any other machine that has Docker installed, regardless of the operating system or any other differences between the machines.

Docker has become very popular in recent years as a way to simplify the process of building, deploying, and running applications.

### Installation

Installation script

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

Run docker as non root user

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

Version

```bash
docker version
```

## Containers

### What is a container?

A Docker container is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, libraries, and settings.

Containers are isolated from each other and from the host environment, so an application running inside a container has no access to the host machine or to other containers. This makes it easy to run multiple applications on the same host machine without them interfering with each other, and it also makes it easy to deploy applications to other machines, because the containerized application will run the same way everywhere.

Docker containers are built from Docker images, which are packages that contain all of the necessary components for an application to run. To create a Docker container, you first need to create a Docker image and then use that image to create one or more containers.

### Running containers

```bash
# Create and start a new container
docker container run IMAGE

# Create and start a new named container
docker container run --name NAME IMAGE

# Create and start a new container with mapped ports
docker container run -p HOSTPORT:CONTAINERPORT IMAGE

# Create and start a new container and map all ports
docker container run -P IMAGE
```

```bash
# Examples
docker container run alpine echo "Hello world"
docker container run centos ping -c 5 127.0.0.1
docker container run -d --name trivia fundamentalsofdocker/trivia:ed2
docker container stop trivia
docker container start trivia
```

### Managing single containers

```bash
# Create a new container
docker container create IMAGE

# Start a container
docker container start CONTAINER

# Gracefully stop a container
docker container stop CONTAINER

# Kill (SIGKILL) a container
docker container kill CONTAINER

# Gracefully stop and restart a container
docker container restart CONTAINER

# Suspend a container
docker container pause CONTAINER

# Resume a container
docker container unpause CONTAINER

# Destroy a container
docker container rm CONTAINER
```

### Managing multiple containers

```bash
# All running containers
docker container COMMAND $(docker container ls -q)
docker COMMAND $(docker ps -q)

# All stopped and running containers
docker container COMMAND $(docker container ls -a -q)
docker COMMAND $(docker ps -a -q)

# Delete all containers including volumes
docker container rm -vf $(docker container ls -a -q)
docker rm -vf $(docker ps -a -q)
```

### Cleanup

```bash
# Delete all dangling and unused images, containers, cache, and volumes
docker system prune

# To delete all used and unused images
docker system prune -a

# To delete all volumes
docker system prune --volumes
```

### Inspecting containers

```bash
# List running containers
docker container ls
docker ps

# List all containers, including stopped
docker container ls -a
docker ps -a

# Show a container output
docker container logs CONTAINER

# Follow a container output
docker container logs -f CONTAINER

# List the processes running in a container
docker container top CONTAINER

# Show the differences with the image (modified files)
docker container diff CONTAINER

# Show information of a container (json formatted)
docker container inspect CONTAINER
```

```bash
# Examples
docker container inspect trivia
docker container inspect -f "{{json .State}}" trivia | jq
docker container logs trivia
docker container logs --tail 5 trivia
docker container logs --tail 5 --follow trivia
```

### Running commands

```bash
# Attach to a container
docker container attach CONTAINER

# Copy files from the container to the host
docker container cp CONTAINER:PATH HOSTPATH

# Copy files from the host to the container
docker container cp HOSTPATH CONTAINER:PATH

# Export the content of the container (tar archive)
docker container export CONTAINER

# Run a command inside a container
docker container exec CONTAINER

# Open an interactive shell inside a container
docker container exec -i -t CONTAINER /bin/bash

# Wait until the container terminates and returns the exit code
docker container wait CONTAINER
```

```bash
# Examples
docker container exec -i -t trivia /bin/sh
docker container exec trivia ps
docker container attach trivia # Ctrl+P + Ctrl+Q to detach
```
