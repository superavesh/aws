# RabbitMQ Image Pull and Run as docker container
```
sudo docker run -d -p 15672:15672 --hostname rabbit --name rabbit rabbitmq:3.8.5-management
```
## if you wants to go inside a container and do some configuration

```
sudo docker exec -it rabbit bash
```
## For checking available Plugins

```
rabbitmq-plugins list
```
## If you want to add extra plugins
```
apt-get update

apt-get install -y curl

curl -L https://github.com/rabbitmq/rabbitmq-delayed-message-exchange/releases/download/v3.8.0/rabbitmq_delayed_message_exchange-3.8.0.ez > $RABBITMQ_HOME/plugins/rabbitmq_delayed_message_exchange-3.8.0.ez

chown rabbitmq:rabbitmq $RABBITMQ_HOME/plugins/rabbitmq_delayed_message_exchange-3.8.0.ez

rabbitmq-plugins enable --offline rabbitmq_delayed_message_exchange
```
