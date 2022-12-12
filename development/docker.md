# Docker

## Introduction

### What is Docker?

Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

This means the application will run on any other machine that has Docker installed, regardless of the operating system or any other differences between the machines.

Docker has become very popular in recent years as a way to simplify the process of building, deploying, and running applications.

## Containers

### What is a container?

A Docker container is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, libraries, and settings.

Containers are isolated from each other and from the host environment, so an application running inside a container has no access to the host machine or to other containers. This makes it easy to run multiple applications on the same host machine without them interfering with each other, and it also makes it easy to deploy applications to other machines, because the containerized application will run the same way everywhere.

Docker containers are built from Docker images, which are packages that contain all of the necessary components for an application to run. To create a Docker container, you first need to create a Docker image and then use that image to create one or more containers.


