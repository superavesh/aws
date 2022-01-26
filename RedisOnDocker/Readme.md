# Redis on Docker

Docker image over [here](https://hub.docker.com/_/redis)

## Running redis
```sh
docker network create redis
docker run -it --rm --name redis --net redis -p 8080:6379 redis:6.0-alpine
```

