# Using Goaccess to tail on logs

Goaccess is a fantastic tool to monitor requests.
In case you have a spike on your system and want to debug which are the most requested pages (in case of a ddos, or something similar) goaccess is fast and easy to use.

```bash
tail -f /var/log/nginx/*.log | goaccess -c
```

and you'll get the tailed info directly on the console stats of goaccess.