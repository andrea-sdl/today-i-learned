# How to fix the could not build optimal proxy_headers_hash #

```
nginx: [warn] could not build optimal proxy_headers_hash, you should increase either proxy_headers_hash_max_size: 512 or proxy_headers_hash_bucket_size: 64; ignoring proxy_headers_hash_bucket_size
```

There are some cases when this error is caused by the number of server names you have in your nginx config.
But if you're not abusing them, the cause is different: there is a duplication in the ```proxy_set_header```
so basically you're setting it twice.

Check the config and remove the duplicates and it should be fixed.

