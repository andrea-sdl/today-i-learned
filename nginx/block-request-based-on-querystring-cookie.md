# Block a request based on the value of a cookie or a query string in Nginx #
```
set $block_banned_affiliates 0;
if ($http_cookie ~* "TEXT" ) {
    set $block_banned_affiliates 1;
}
if ($query_string ~ "TEXT" {
    set $block_banned_affiliates 1;
}
if ($block_banned_affiliates = 1) {
    return 403;
}
```