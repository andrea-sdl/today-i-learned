# Ban access to the xmlrpc.php wordpress file using fail2ban + nginx #

Simple and quick fix to avoid being flooded by xmlrpc requests.

```
#/etc/fail2ban/jail.local

....

[web-xmlrpc]
enabled = true
port = http,https
filter = web-xmlrpc
logpath = /var/log/nginx/*access.log
maxretry = 6
```

```
#/etc/fail2ban/filter.d/web-xmlrpc.conf

[Definition]
failregex = (<HOST>) -.*POST.*xmlrpc\.php.*
ignoreregex =
```