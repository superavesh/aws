
## Replication

Documentation [here](https://redis.io/topics/replication)

### Configuration

```
#persistence
dir /data
dbfilename dump.rdb
appendonly yes
appendfilename "appendonly.aof"

```
### redis-master Configuration

```
port 8081

#authentication
requirepass a-very-complex-password-here
```
### redis-slave Configuration

```
port 8082
slaveof redis-master 8081

#authentication
masterauth a-very-complex-password-here
requirepass a-very-complex-password-here

```

```

# remember to update above in configs!

sudo docker run -d -p 8081:8081 --name redis-master -v ${PWD}/Master/config:/etc/redis/ redis:6.0-alpine redis-server /etc/redis/redis.conf

sudo docker run -d -p 8082:8082 --name redis-slave -v ${PWD}/Slave/config:/etc/redis/ redis:6.0-alpine redis-server /etc/redis/redis.conf

sudo docker run -d -p 8083:8083 --name sentinel01 -v ${PWD}/Sentinel01/config:/etc/redis/ redis:6.0-alpine redis-sentinel /etc/redis/sentinel.conf

sudo docker run -d -p 8084:8084 --name sentinel02 -v ${PWD}/Sentinel02/config:/etc/redis/ redis:6.0-alpine redis-sentinel /etc/redis/sentinel.conf

sudo docker run -d -p 8085:8085 --name sentinel03 -v ${PWD}/Sentinel03/config:/etc/redis/ redis:6.0-alpine redis-sentinel /etc/redis/sentinel.conf






sudo docker exec -it sentinel01 sh

redis-cli -h 127.0.0.1 -p 8082 -a zaLq6IsUlvqnpT3lYekAWAChKxwPhAtIjjng3HszVWY= ping

redis-cli -h 127.0.0.1 -p 8082 -a zaLq6IsUlvqnpT3lYekAWAChKxwPhAtIjjng3HszVWY=

redis-cli -h 127.0.0.1 -p 8083 ping

redis-cli -h 127.0.0.1 -p 8083

```

## Additional Info

Run example application in video, to show application writing to the master

```
cd .\storage\redis\applications\client\
docker build . -t aimvector/redis-client:v1.0.0

docker run -it --net redis `
-e REDIS_HOST=redis-0 `
-e REDIS_PORT=6379 `
-e REDIS_PASSWORD="a-very-complex-password-here" `
-p 80:80 `
aimvector/redis-client:v1.0.0

```

## Test Replication

Technically written data should now be on the replicas

```
# go to one of the clients
docker exec -it redis-2 sh
redis-cli
auth "a-very-complex-password-here"
keys *

```

## Running Sentinels

Documentation [here](https://redis.io/topics/sentinel)

```
#********BASIC CONFIG************************************
port 5000
sentinel monitor mymaster redis-0 6379 2
sentinel down-after-milliseconds mymaster 5000
sentinel failover-timeout mymaster 60000
sentinel parallel-syncs mymaster 1
sentinel auth-pass mymaster a-very-complex-password-here
#********************************************

```
Starting Redis in sentinel mode

```
cd .\storage\redis\clustering\

docker run -d --rm --name sentinel-0 --net redis `
    -v ${PWD}/sentinel-0:/etc/redis/ `
    redis:6.0-alpine `
    redis-sentinel /etc/redis/sentinel.conf

docker run -d --rm --name sentinel-1 --net redis `
    -v ${PWD}/sentinel-1:/etc/redis/ `
    redis:6.0-alpine `
    redis-sentinel /etc/redis/sentinel.conf

docker run -d --rm --name sentinel-2 --net redis `
    -v ${PWD}/sentinel-2:/etc/redis/ `
    redis:6.0-alpine `
    redis-sentinel /etc/redis/sentinel.conf


docker logs sentinel-0
docker exec -it sentinel-0 sh
redis-cli -p 5000
info
sentinel master mymaster

# clean up 

docker rm -f redis-0 redis-1 redis-2
docker rm -f sentinel-0 sentinel-1 sentinel-2


```
