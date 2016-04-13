# Class *Seeder does not exist - How to fix it#

If multiple people work on the same project with laravel/composer, composer might throw an exception of class not found.

This is because composer keeps a list of the autoloaded classes that it knows.

To fix this, you have to type
```
composer dump-autoload
```

this will recreate the class list