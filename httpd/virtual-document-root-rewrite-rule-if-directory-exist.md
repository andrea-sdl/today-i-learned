# How to do a RewriteRule when using a VirtualDocumentRoot in Apache 2.2 

VirtualDocumentRoot is a nice feature, but it has its drawbacks, one of them is that "DOCUMENT_ROOT" is not correctly setup. 

Lately I had the need to do a Rewrite ONLY if the directory did exist, which is a data that's not available in any apache variable.

To fix it the only way is to duplicate the logic of the VirtualDocumentRoot inside the rewrite cond.

So, let's say that we use a path like this
```/var/www/{1}/{2}/{3}/{thirdleveldomain}```
where {1,2,3} are the first 3 characters of our third level domain (if we use "thirdleveldomain.example.com" they would be 't' 'h' 'i')

The VirtualDocumentRoot would be 
```VirtualDocumentRoot /var/www/%1.1/%1.2/%1.3/%1/```

To do a rewrite that applies to a page ONLY IF the directory exist, we could then do

```
#Checks the page to redirect
RewriteCond %{REQUEST_FILENAME} ^/page-match.html$
# creates the matching for the first 3 chars "and the rest"
RewriteCond %{HTTP_HOST} ^([^\.])([^\.])([^\.])([^\.]*)\..*$ [NC]
# uses them to build the path and check it exists
RewriteCond /var/www/%1/%2/%3/%1%2%3%4/ -d
# redirects (PT is added to allow evaluating Alias directives, if present.)
RewriteRule (.*) /redirected-page.html [PT]
```
and that's it.

