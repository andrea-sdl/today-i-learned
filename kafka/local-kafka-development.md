# Starting a local kafka cluster with kafka manager

Kafka seems like a complex system to startup, but if you have docker everything becomes easy. 

When I searched I stumbled upon the great work of https://github.com/simplesteph/kafka-stack-docker-compose
but I thought it would be nice to have also kafkamanager so we could also gain some insight on how the local kafka was working.

Therefore I added to the yml and fixed it. 

To execute simply download the [docker-kafka-with-kafkamanager.yml](docker-kafka-with-kafkamanager.yml) and execute the command
`docker-compose -f docker-kafka-with-kafkamanager.yml up`

and to stop it do
`docker-compose -f docker-kafka-with-kafkamanager.yml down`

Kafka is available on port 9092/9093, zoo on 2181 and kafka manager on localhost:9000