# What if intellij doesn't attach the breakpoints correctly?

If you're using intellij community edition and you find that, after configuring the maven goal 
```spring-boot:run``` it doesn't work, it might be because spring sometimes forks the process.

This leads to IntellJ listening to the wrong JVM.

To fix it change
```spring-boot:run```
to
```spring-boot:run -Dfork=false```