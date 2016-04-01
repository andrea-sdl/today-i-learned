# Check the result of a program execution #

I had the need to do a more complex check with monit, to do that I created a small php file (but could be bash, anything), that returns 0 if ok, and another number if error.

Useful when you need to test real world scenario cases.
Remember to make the PHP file executable.

## monit config##
```
check program program2test with path "/home/user/program2test.php"
        if status != 0 then alert 
```

```php
#!/usr/bin/php -q
<?php
//...your code..

if($errorCondition) exit(1);

exit(0);
?> 
```
