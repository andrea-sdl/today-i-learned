# How to issue a wildcard certificate with letsencrypt

Creating a wildcard requires a little bit extra data in the command line

```
sudo certbot-auto certonly --manual --preferred-challenges=dns --email youremail@example.com --server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d *.domain.com
```

After that you'll be prompted to create a TXT Record, create it before continuing, and then you'll have the certificate under the
`/etc/letsencrypt/live/domain.com/` folder