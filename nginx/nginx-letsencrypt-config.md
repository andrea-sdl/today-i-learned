# How to use the generated letsencrypt chain in NGINX #

```
  ssl_certificate       /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
  ssl_certificate_key   /etc/letsencrypt/live/yourdomain.com/privkey.pem;
```