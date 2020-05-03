# Docker

> "_[Docker](https://docker.com) can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession._"

## Table of Contents
1. [Dockerfile](#docker-file)
   1. [Environment Variables](#environment-variables)
   1. [Language](#language)
   1. [Commands](#commands)
1. [Cloud Native Buildpacks](#cloud-native-buildpacks)   

## Dockerfile
### Environment Variables
> A valid Dockerfile must start with a FROM instruction.
* `ADD`
* `COPY`
* `ENV`
* `EXPOSE`
* `FROM`  
* `LABEL`
* `STOPSIGNAL`
* `USER`
* `VOLUME`
* `WORKDIR`
* `ONBUILD`
### Language
* [Ruby](https://hub.docker.com/_/ruby)  
```dockerfile
FROM ruby:2.7.1
RUN apt-get update -qq && apt-get install -y \
  nodejs \
  libpq-dev \
  postgresql-client \
  build-essential
```
### Commands
* `build`  
```bash
$ docker build .
$ docker build -f /path/to/a/Dockerfile .
```
### Ignore
The `.dockerignore` belongs in the root directory.
```docker
*/tmp*
*/*/tmp*
tmp?
```

## Cloud Native Buildpacks
[Buildpacks](https://buildpacks.io) are pluggable, modular tools that translate source code into OCI images.
```bash
pack build app --builder heroku/buildpacks:18
docker run app
```