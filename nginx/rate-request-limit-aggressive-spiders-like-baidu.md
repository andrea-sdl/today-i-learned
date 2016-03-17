# Limit the requests that come from a too aggressive spider #

Two configs to limit the over-aggressive spiders (in this case I chose baidu/yandex as example, but you can put anything).

Quick notes
* the "map" functions allows to pass the user_agent and limit based on that, instead of the IP.
* if we pass an empty value to $limit_bots the limit_req_zone will ignore that value (that's why it works)
* rate limited to 5 request per minute 
* the nodelay option means it will give a 503 if it exceeds,otherwise it waits to be completed 
* 10m is the dimension of the zone (10 megabytes)
* bursts allows some spikes (in this case 3 additional request)

#### First config ####
```
http {
        #...your config
        
        map $http_user_agent $limit_bots {
            default '';
            ~*(yandex|baidu) $http_user_agent;
        }

        limit_req_zone $limit_bots zone=bots:10m rate=5r/m;
}
```

#### Second config ####
```
location / {
    #..your config...
    limit_req zone=bots burst=3 nodelay;
}
```