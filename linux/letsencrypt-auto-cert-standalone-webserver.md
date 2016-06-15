# Setup letsencrypt/certbot with a server with no integration #

Quick & dirty script with multiple domains
```bash
sudo ./letsencrypt-auto certonly --email admin@yourdomain.com --webroot -w /var/www/yourdomain.com/ -d www.yourdomain.com -d yourdomain.com -w /var/www/second-domain.com/ -d www.second-domain.com
```

For certbot replace letsencrypt with certbot :)

the files are then put into
```
/etc/letsencrypt/live/yourdomain.com/fullchain.pem;
/etc/letsencrypt/live/yourdomain.com/privkey.pem;
```