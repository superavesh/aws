# Redis on Docker

Docker image over [here](https://hub.docker.com/_/redis)

## Running redis
```sh
docker network create redis
docker run -it --rm --name redis --net redis -p 8080:6379 redis:6.0-alpine
```
## Configuration
Redis configuration documentation [here](https://redis.io/topics/config)

Starting Redis with a custom config

```sh
cd .\storage\redis\
docker run -it --rm --name redis --net redis -v ${PWD}/config:/etc/redis/ redis:6.0-alpine redis-server /etc/redis/redis.conf
```

## Security
Redis should not be exposed to public. Always use a strong password in `redis.conf`

```sh
requirepass SuperSecretSecureStrongPass
```

## Persistence

Redis Persistence Documentation [here](https://redis.io/topics/persistence)

```sh
docker volume create redis
cd .\storage\redis\
docker run -it --rm --name redis --net redis -v ${PWD}/config:/etc/redis/ -v redis:/data/  redis:6.0-alpine redis-server /etc/redis/redis.conf
```

## Redis Replication and High Availability
Lets move on to the [clustering](https://github.com/superavesh/aws/blob/1ff77668454e91bb6dfb0d9f2df807f115272e6c/Redis%20On%20Docker/Clustering/README.md) secion.
