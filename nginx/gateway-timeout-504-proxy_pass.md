# Gateway timeout 504 error and how to extend the timemout when using proxy_pass #

Simple config, you can use the number of seconds or add some time measure (like hours) so it's readable.

```
proxy_send_timeout          1h;
proxy_read_timeout          1h;
send_timeout                1h;
```