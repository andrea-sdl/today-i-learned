# Whitelisting Cloudflare / Jetpack in fail2ban #

If you ever used fail2ban here's a list of ips you might want to ignore given the fact that they're from wordpress.com/cloudflare.

The file to edit is the _jail.local_

```
[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host. Fail2ban will not
# ban a host which matches an address in this list. Several addresses can be
# defined using space separator.
ignoreip = 127.0.0.1/8 185.64.140.0/22 199.27.128.0/21 173.245.48.0/20 103.21.244.0/22 103.22.200.0/22 103.31.4.0/22 141.101.64.0/18 108.162.192.0/18 190.93.240.0/20 188.114.96.0/20 197.234.240.0/22 198.41.128.0/17 162.158.0.0/15 104.16.0.0/12 172.64.0.0/13
```