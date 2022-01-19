# AWS
This Project is for Learning Redis, RabbitMQ, ASPNET Core, Docker and K8s

## Redis on Docker

Docker image over [here](https://hub.docker.com/_/redis)

## Running redis
```sh
docker network create redis
docker run -it --rm --name redis --net redis -p 6379:6379 redis:6.0-alpine
```
