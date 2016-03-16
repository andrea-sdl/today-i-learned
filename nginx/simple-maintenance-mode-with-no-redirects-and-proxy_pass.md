# Simple maintenance mode in nginx with no redirects #

This is a quick mix of a possible maintenance mode that's a bit more advanced than usual.

It includes :
* a file to check and for a cookie (*maintenance.mode*)
* the ability to skip the maintenance if you visit the url */no_maintenance_mode.html*
* no redirects, it uses instead a proxy pass to "outsource" the page from other domains too.
* doesn't return 503 error but instead a 200
* example on how to exclude an ip from the maintenance 

**the resolver part can be removed if you don't need to generalize the urls**

```
set $maintenance_host yourmaintenancedomain.com;
set $maintenance_uri /url/maintenance.html;

 location / {
    #
    # ... your other config
    #
    
    set $maintenance 0;
    location /no_maintenance_mode.html{
    add_header Set-Cookie AllowMaintenance=1;
    return 302 /;
    }

    if ( -f $document_root/maintenance.mode){
        set $maintenance 1;
    }

    if ($cookie_AllowMaintenance = '1'){
        set $maintenance 0;
    }

    if ($remote_addr = '127.0.0.1'){
        set $maintenance 0;
    }

    if ($maintenance = 1){
        return 503;
    }
 }
 
error_page 503 =200 @maintenance;
location @maintenance{
  resolver           8.8.8.8;      #necessary when we use variables in proxy_pass
  proxy_pass         http://$maintenance_host$maintenance_uri;
  proxy_set_header   Host $maintenance_host;
}
```