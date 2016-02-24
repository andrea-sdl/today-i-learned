## Reset root mysql password on Linux systems ##

```bash
service mysqld stop
/usr/bin/mysqld_safe --skip-grant-tables 
```

on another terminal

```bash mysql```
```mysql
connect mysql;
UPDATE user SET Password=PASSWORD('newpass') WHERE User='root';
```

then ctrl+c the mysqld_safe and start mysql again
