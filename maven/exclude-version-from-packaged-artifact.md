# Exclude the version from the jar

If you don't want the version in the resulting package maven when you do
```
mvn package
```

you only have to add the finalname to the build phase. (works also on springboot)


```
    <build>
        <finalName>${project.artifactId}</finalName>
        <!--...-->
    </build>
```