# Accessing spring 4 env properties from thymeleaf

quite a simple code 

```java
${@environment.getProperty('app.env')}
```