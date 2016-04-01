# Print the X-Forwarded-For Header in the apache logs #

SinceIwe had a config with a balancer in front of two servers I wanted to print the real IP address of the user, and not the balancer one.

To do that I created a new LogFormat by copying the default apache ones, and added the _%{X-Forwarded-For}i_ in front of it.
Note that I also added the _%h_ at the end to be sure that also the balancer ip gets printed, to be sure.

The second line setup an env variable that says that checks the headers and is set when the header X-Forwarded-For is present.

THe last 2 lines choose which log to use based on the env variable

```
LogFormat "%{X-Forwarded-For}i %l %u %t \"%r\" %>s %b %h" commonBalancer
SetEnvIf X-Forwarded-For "^.*\..*\..*\..*" forwarded
CustomLog "logs/access_log" common env=!forwarded
CustomLog "logs/access_log" commonBalancer env=forwarded
```