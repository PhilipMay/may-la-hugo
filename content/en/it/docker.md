---
title: Docker
---

## Commands
- build: `docker build . -t <tag_name>`
- connect to a container: `docker exec -it <container_name> bash`
- delete
  - delete all volumes: `docker volume rm $(docker volume ls -q)` - [docker volume rm](https://docs.docker.com/engine/reference/commandline/volume_rm/) - [docker volume ls](https://docs.docker.com/engine/reference/commandline/volume_ls/)
  - delete all: `docker stop $(docker ps -aq) && docker rm $(docker ps -aq) && docker rmi $(docker images -q)`
- list containers - [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
  - list running containers: `docker ps`
  - list all containers: `docker ps -a`

## Dockerfile
- set variables: `ARG variable=value`
- use variables example: `WORKDIR /home/$variable`

## docker-compose
- https://docs.docker.com/compose/
- store config in `docker-compose.yml` by defaut
- start (build images before starting containers): `docker-compose up --build` - [docker-compose up](https://docs.docker.com/compose/reference/up/)
  - add `-d` for detached mode
- stop
  - stop and remove containers: `docker-compose down` - [docker-compose down](https://docs.docker.com/compose/reference/down/)
  - stop and remove containers and volumes: `docker-compose down -v` - [docker-compose down](https://docs.docker.com/compose/reference/down/)
- validate and view compose file: `docker-compose config` - [docker-compose config](https://docs.docker.com/compose/reference/config/)
