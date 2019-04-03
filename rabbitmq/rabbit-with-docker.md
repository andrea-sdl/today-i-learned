# Execute local rabbitmq with docker

This is a very simple oneliner. 
Basically the rabbit-compose.yml contains a simple rabbitmq server to execute, available locally and with user/password "rabbitmq-admin"

```sh
docker-compose -f rabbit-compose.yml up
```