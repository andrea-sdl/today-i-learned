# Forward the client ip when tomcat is behind nginx through the proxy pass #

If you use tomcat and the proxy_pass directive in nginx chances are you'll get a strange result when calling ```request.getRemoteAddr```
this is because nginx need to pass the new ip to the client.


Here it is the required nginx config to allow it to pass the information onto the tomcat.
```
proxy_set_header Host $host:$server_port;
proxy_set_header  X-Real-IP $remote_addr;
proxy_set_header  X-Forwarded-For $remote_addr;
proxy_set_header  X-Forwarded-Host $remote_addr;

proxy_pass http://127.0.0.1:8080;
```

**notes**
If you use *localhost* in the proxy_pass beware that for reasons unknown to me sometimes it gets mapped to the ipv6 interface and the default config of the RemoteIpValve is not so smart to know it's still localhost.
A workaround is tu use the direct ip *127.0.0.1*.



Also, in the *context.xml* of tomcat you can use the RemoteIpValve to convert the ip.

```xml
<Valve className="org.apache.catalina.valves.RemoteIpValve"
                       remoteIpHeader="x-forwarded-for"
                       requestAttributesEnabled="true" />
```

**notes**
for the remoteIpHeader you can use both 'x-forwarded-for' or 'X-REAL-IP', the former should contain all the chain of forwarded ip.


## Addon if nginx is behind a balancer or a proxy ##

If nginx is behind a balancer or a proxy then you have to use the realip module

```
#trust anyone
set_real_ip_from 0.0.0.0/0

#trust a subnet
set_real_ip_from  192.168.1.0/24;

#trust an ip
set_real_ip_from  192.168.2.1;
set_real_ip_from  2001:0db8::/32;

#the header to use
real_ip_header    X-Forwarded-For;
real_ip_recursive on;
```