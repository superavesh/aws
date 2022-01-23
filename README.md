# AWS
This Project is for Learning Redis, RabbitMQ, ASPNET Core, Docker and K8s

## Road Map to do this project

- [Business Model](#BusinessModel)
- [Monolithic Architecture](#MonolithicArchitecture)
- [Microservice Architecture](#MicroserviceArchitecture)
- [Role of Containers](#RoleofContainers)
- [Docker](#Docker)
- [Kubernates](#Kubernates)
- [AWS part](#AWS part)
- [Redis on docker](#Redis on docker)
- [Redis Cluster and Persistence](#Redis Cluster and Persistence)
- [RabbitMQ on Docker](#RabbitMQ on Docker)
- [RabbitMQ Cluster and Miroring](#RabbitMQ Cluster and Miroring)
- [NFSShared on Docker](#NFSShared on Docker)
- [Port Opening between containers](#Port Opening between containers)
- [database odbc port opening inside containers](#database odbc port opening inside containers)
- [API on Docker](#API on Docker)
- [Vue JS Websites on Docker](#Vue JS Websites on Docker)
- [Background Services on Docker with config file for different containers](#Background Services on Docker with config file for different containers)
- [Testing](#Testing)
- [Documentation](#Documentation)

## Redis on Docker

Docker image over [here](https://hub.docker.com/_/redis)

## Running redis
```sh
docker network create redis
docker run -it --rm --name redis --net redis -p 8080:6379 redis:6.0-alpine
```
