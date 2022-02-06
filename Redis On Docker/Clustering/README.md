
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


