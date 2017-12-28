# How to have multiple if conditions in nginx

This is a great (but absolutely terrible) trick for those cases when you want a more complex if in nginx.

It shouldn't be used lightly.

Anyway, the trick is based upon simple string concatenation and it allows to have complex ifs in nginx by simply checking for the final string of that concatenation.
```
  if ($scheme != "https") {
    set $redirectHttpsCondition 'ssl';
  }
  if ( $request_uri !~ '/public/.*' ){
    set $redirectHttpsCondition '${redirectHttpsCondition}+notdynamic';
  }

  if ( $redirectHttpsCondition = 'ssl+notdynamic' ){
    return 301 https://$host$request_uri;
  }
```
