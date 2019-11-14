# Support spring boot mvn debugging in intellij idea Community Edition

For some reasons intellij CE doesn't debug correctly projects runned by maven spring-boot:run.
The reason lies in the forking that happens when it's managed by the spring boot run command.

To avoid this, add these parameters to the execution

## Spring boot 2.0-2.1
`-Dfork=false`

## Spring boot 2.2
`-Dspring-boot.run.fork=false`