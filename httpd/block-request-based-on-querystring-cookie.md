# Block a request based on the value of a cookie or a query string in HTTPD #

```
<IfModule mod_rewrite.c>
 RewriteEngine On
 RewriteCond %{QUERY_STRING} TEXT [NC]
 RewriteRule ^(.*)$ - [F,L]
 RewriteCond %{HTTP_COOKIE} TEXT [NC]
 RewriteRule ^(.*)$ - [F,L]
</IfModule>
```

