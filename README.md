# AWS
This Project is for Learning Redis, RabbitMQ, ASPNET Core, Docker and K8s

## Road Map to do this project

- [Business Model](#BusinessModel)
- [Monolithic Architecture](#MonolithicArchitecture)
- [Microservice Architecture](#MicroserviceArchitecture)
- [Role of Containers](#RoleofContainers)
- [Docker](#Docker)
- [Kubernates](#Kubernates)
- [AWS part](#AWSpart)
- [Redis on docker](#RedisOnDocker)
- [Redis Cluster and Persistence](#RedisClusterAndPersistence)
- [RabbitMQ on Docker](#RabbitMQOnDocker)
- [RabbitMQ Cluster and Miroring](#RabbitMQClusterAndMiroring)
- [NFSShared on Docker](#NFSSharedOnDocker)
- [Port Opening between containers](#PortOpeningBetweenContainers)
- [database odbc port opening inside containers](#databaseOdbcPortOpeningInsideContainers)
- [API on Docker](#APIOnDocker)
- [Vue JS Websites on Docker](#VueJSWebsitesOnDocker)
- [Background Services on Docker with config file for different containers](#BackgroundServicesOnDockerWithConfigFileForDifferentContainers)
- [Testing](#Testing)
- [Documentation](#Documentation)

## Redis on Docker

Docker image over [here](https://hub.docker.com/_/redis)

## Running redis
```sh
docker network create redis
docker run -it --rm --name redis --net redis -p 8080:6379 redis:6.0-alpine
```
