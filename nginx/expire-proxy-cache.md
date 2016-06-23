# Expired a cached page from the proxy_cache #

If you have a proxy cache active and correctly configured then you can add this
```
proxy_cache_bypass http_secret_header;
```

to have a header to bypass the cache.

And if you also have

```
add_header X-Proxy-Cache $upstream_cache_status;
```
you can see what's the cache status for that page.

Once this is setup, you can use a simple curl call

```bash
curl http://www.domain.com/yourpage.html -s -I -H "secret-header:true"
```
The options for curl are in this case
* -s : silent
* -I : only show Head
* -H : pass custom header line (required to bypass the cache)

That's it!