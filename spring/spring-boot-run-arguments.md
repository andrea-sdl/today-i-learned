# Overriding properties as arguments while running spring boot.

Let's say you want to override some nested property saved in your spring application.yml while running 
`mvn spring-boot:run`

one way is to add the `-Dspring-boot.run.arguments=` so that your arguments override directly the information placed in the config.

This is useful in case you don't want to create ad-hoc profiles for spring (like personal configs), or add some extra info related to the machine you're working on, or test to do.

here's an example of an override of kafka servers and brokers

`mvn spring-boot:run -Dspring-boot.run.arguments=--spring.kafka.bootstrap-servers=localhost:9092,--spring.cloud.stream.kafka.binder.brokers=localhost:9092`